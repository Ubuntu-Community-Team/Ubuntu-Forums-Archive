---
title: "Certificate trouble with Java in 9.10 but not 8.04"
date: 2009-12-22
forum: General Help
---

### Post by proctorsilex on 2009-12-22
I was using Ubuntu 8.04 for developing a Java application that communicates with an HTTPS server that has a certificate. The network does not have a local DNS, so I have to reference by its IP address. The server's certificate does not include its IP address in the CN, so I have to keep an entry for it in the Java client's key store with the alias as the IP address. This setup worked in Ubuntu 8.04 with Java 1.6_17. It has also worked in MS Windows (XP and Vista) and for customers.

I upgraded to Ubuntu 9.10 and found that the Java client fails with the following error:
```
     [java] org.mozilla.javascript.WrappedException: Wrapped com.sun.xml.internal.ws.client.ClientTransportException: HTTP transport error:
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException:
No subject alternative names present (10.0.0.101#6)
```I had not changed the client or the key store at all. I tried unlocking my Java package in Synaptic to install Java 1.6_15 (I think) that 9.10 uses; I tried other JDKs directly from Sun; none of them worked either.

I can connect to the exact same HTTPS URL in Firefox without any problem: I can see the expected data.

I tried setting the server's certificate CN to the server's IP address, but that failed with the same error.

After much frustration, I found that the server's certificate had to have a Subject Alternative Name set to the server's IP address.

Why did the exact same setup work in 8.04 but fail in 9.10?

Why does Firefox accept the certificate while Java does not? Remember that the JRE/JDK did not change between upgrading for me. Also, other older versions of Java fail in 9.10. I am presuming that it has something to do with a change in GNUTLS or OpenSSL, but I do not know which one Sun's Java uses (Firefox is linked to GNUTLS).

The server is a production device so I cannot easily change the certificate. I need to know why the behaviour changed: whether it is a bug or as specified by RFC. I also need to know whether it can be worked around from the client end.

Thank you

---

### Post by Dobi_pt on 2010-02-02
> **proctorsilex said:**
> 
After much frustration, I found that the server's certificate had to have a Subject Alternative Name set to the server's IP address.
Thank you

Hi proctorsilex,

Unfortunatly I dont have an answer for you but a question. 
I think that I have the same problem...

With java I have to access to this link "https://192.168.0.10/sys/GetLoginData.js" and read its content, I have a self signed certificate that is already in the keystore (I use keytool to put it in "../jre6/security/cacerts". When I execute my simple program to read the contentthe result is "...No subject alternative names present".

How can I set the name as you mention before?

Thanks in advance.

Cheers

My certificate:
[IMG]http://i47.tinypic.com/2u4msqo.png[/IMG]

---

