---
title: "Mono 2.6.3 Gmail certificate not working"
date: 2010-06-25
forum: General Help
---

### Post by Wien Smit on 2010-06-25
Hi all,

i have a fairly simple asp.net website with a contact form all worked fine until Google updated there certificate needed to make use of there gmail smtp server.
now i have installed mono 2.6.3 on ubuntu 10.04 with the help of badgerpors and i have imported the certificates with the following results:



certmgr -ssl -m  smtps://smtp.gmail.com:465
Mono Certificate Manager - version 2.6.3.0
Manage X.509 certificates and CRL from stores.
Copyright 2002, 2003 Motus Technologies. Copyright 2004-2008 Novell. BSD licensed.


 X.509 Certificate v3
   Issued from: C=US, O=Equifax, OU=Equifax Secure Certificate Authority
   Issued to:   C=US, O=Google Inc, CN=Google Internet Authority
   Valid from:  6/8/2009 10:43:27 PM
   Valid until: 6/7/2013 9:43:27 PM
   *** WARNING: Certificate signature is INVALID ***
This certificate is already in the CA store.

 X.509 Certificate v3
   Issued from: C=US, O=Google Inc, CN=Google Internet Authority
   Issued to:   C=US, S=California, L=Mountain View, O=Google Inc, CN=smtp.gmail.com
   Valid from:  4/22/2010 10:02:45 PM
   Valid until: 4/22/2011 10:12:45 PM
This certificate is already in the AddressBook store.

No certificate were added to the stores.

if i am correct the certificate is invalid waring is only about the selfsigned
so hopefully that would mean that the certificates are there.
still when i try to use the contact form and send a mail i get the following:


System.Net.Mail.SmtpException: Message could not be sent. ---> System.IO.IOException: The authentication or decryption has failed. ---> System.InvalidOperationException: SSL authentication error: RemoteCertificateNotAvailable at System.Net.Mail.SmtpClient.m__3 (System.Object sender, System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Security.Cryptography.X509Certificates.X509Chain chain, SslPolicyErrors sslPolicyErrors) [0x00000] in :0 at System.Net.Security.SslStream+c__AnonStorey7.<>m__9 (System.Security.Cryptography.X509Certificates.X509Certificate cert, System.Int32[] certErrors) [0x00000] in :0 at Mono.Security.Protocol.Tls.SslClientStream.OnRemoteCertificateValidation (System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Int32[] errors) [0x00000] in :0 at Mono.Security.Protocol.Tls.SslStreamBase.RaiseRemoteCertificateValidation (System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Int32[] errors) [0x00000] in :0 at Mono.Security.Protocol.Tls.SslClientStream.RaiseServerCertificateValidation (System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Int32[] certificateErrors) [0x00000] in :0 at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.validateCertificates (Mono.Security.X509.X509CertificateCollection certificates) [0x00000] in :0 at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.ProcessAsTls1 () [0x00000] in :0 at Mono.Security.Protocol.Tls.Handshake.HandshakeMessage.Process () [0x00000] in :0 at (wrapper remoting-invoke-with-check) Mono.Security.Protocol.Tls.Handshake.HandshakeMessage:Process () at Mono.Security.Protocol.Tls.ClientRecordProtocol.ProcessHandshakeMessage (Mono.Security.Protocol.Tls.TlsStream handMsg) [0x00000] in :0 at Mono.Security.Protocol.Tls.RecordProtocol.InternalReceiveRecordCallback (IAsyncResult asyncResult) [0x00000] in :0 --- End of inner exception stack trace --- at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHandshakeCallback (IAsyncResult asyncResult) [0x00000] in :0 --- End of inner exception stack trace --- at System.Net.Mail.SmtpClient.Send (System.Net.Mail.MailMessage message) [0x00000] in :0 at website.Contact.btnVer_Click (System.Object sender, System.EventArgs e) [0x00000] in :0


the way i read it it seems that i somehow cant find the certificates or something like that
anyway someone here who knows what the heck im doing wrong ?

---

