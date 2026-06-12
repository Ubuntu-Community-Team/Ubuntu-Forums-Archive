---
title: "Error while sendig mail with ssmtp"
date: 2011-06-01
forum: General Help
---

### Post by JCM_Pico on 2011-06-01
I'm trying to send mail from a command with ssmt, but an error is always given:

```

ssmtp -v outside@mail.com < any.txt 
[<-] 220 mx.google.com ESMTP e1sm900739wbh.5
[->] EHLO weather-pirate
[<-] 250 ENHANCEDSTATUSCODES
[->] STARTTLS
[<-] 220 2.0.0 Ready to start TLS
[->] EHLO weather-pirate
[<-] 250 ENHANCEDSTATUSCODES
[->] AUTH LOGIN
[<-] 334 VXNlcm5hbWU6
[->] d2VhdGhlci5waXJhdGUuYXpAZ21haWwuY29t
[<-] 334 UGFzc3dvcmQ6
[<-] 535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 e1sm900739wbh.5
ssmtp: Authorization failed (535 5.7.1 http://mail.google.com/support/bin/answer.py?answer=14257 e1sm900739wbh.5)
```

Did the configuration of ssmtp.config like this:

```
root=myemailaddress@gmail.com
mailhub=smtp.gmail.com:587
AuthUser=mygmailusername
AuthPass=mypassword
UseSTARTTLS=YES
```

Do anybody knows how to fix this?

---

