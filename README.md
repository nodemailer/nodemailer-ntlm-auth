# NTLM authentication for Nodemailer

Nodemailer 5+ allows to use custom authentication mechanisms. While there is no support in Nodemailer for NTLM then it can be provided with an addon.

> **NB!** Experimental! Might not work as advertised due to the lack of not being actually able to use any real NTLM capable server

## Install

Requires Nodejs v8.0.0 or newer

```
npm install nodemailer-ntlm-auth
```

## Usage

```
const nodemailer = require('nodemailer');
const nodemailerNTLMAuth = require('nodemailer-ntlm-auth');

let transporter = nodemailer.createTransport({
    host: 'smtp.example.com',
    port: 465,
    secure: true,
    auth: {
        type: 'custom',
        method: 'NTLM',
        user: 'username',
        pass: 'verysecret',
        options: {
            domain: 'my-domain',
            workstation: 'my-desktop'
        }
    },
    customAuth: {
        NTLM: nodemailerNTLMAuth
    }
});

transporter.sendMail({
    from: 'sender@example.com',
    to: 'recipient@example.com',
    subject: 'hello world!',
    text: 'hello!'
}, console.log)
```
