---
title: "JBOSS Installation"
date: 2010-10-22
forum: General Help
---

### Post by miko5054 on 2010-10-22
im using ubuntu and i guess im doing something wrong and eclipse 
dont recognize the jboss class-path that i set....
can u guide me how to install jboss


update::

i fixed the tool and i can create  new server but it unable to start properly 

>     DEPLOYMENTS IN ERROR:
  Deployment "interface javax.transaction.TransactionManager" is in error due to the following reason(s): ** NOT FOUND Depends on 'interface javax.transaction.TransactionManager' **
  Deployment "TransactionManager" is in error due to the following reason(s): java.lang.ExceptionInInitializerError: java.net.MalformedURLException: no protocol: /home/mik/&#1492;&#1493;&#1512;&#1491;&#1493;&#1514;/jboss-5.1.0.GA/server/default/conf/jbossts-properties.xml, **ERROR**
  Deployment "jboss.jca:service=WorkManager" is in error due to the following reason(s): ** NOT FOUND Depends on 'jboss.jca:service=WorkManager' **
  Deployment "jboss:service=invoker,type=unified" is in error due to the following reason(s): Configured
  Deployment "<UNKNOWN DefaultUserTransactionprovider>" is in error due to the following reason(s): ** UNRESOLVED Demands 'TransactionManager' **
  Deployment "jboss:service=TransactionManager" is in error due to the following reason(s): ** NOT FOUND Depends on 'jboss:service=TransactionManager' **
  Deployment "jboss.jca:service=CachedConnectionManager" is in error due to the following reason(s): ** NOT FOUND Depends on 'jboss.jca:service=CachedConnectionManager' **
  Deployment "jboss.web:service=WebServer" is in error due to the following reason(s): Configured 

thanks 
miki

---

