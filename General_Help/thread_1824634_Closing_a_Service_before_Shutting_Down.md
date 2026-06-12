---
title: "Closing a Service before Shutting Down"
date: 2011-08-14
forum: General Help
---

### Post by AndrewBorg on 2011-08-14
Hi Guys,

I am encountering a Problem with the TeamSpeak server that I host on my Ubuntu Machine. The Problem I'm having is that when I restart the Computer before Stopping the Service from the Terminal, The Server would encounter an error the next time it is started.

With your help I would like to know if there is a File somewhere that is run when the User want to Reboot or Shutdown the PC, or if I can write a script that runs before Shutting down.

Thanks in Advance

Andrew Borg

---

### Post by raja.genupula on 2011-08-14
write the script as write the code for what operation you wanna do and then in the last line place the shutdown command 


so your system will do that function for you and it will shutdown . nothing but the operation before shutdown as you asked 

here is the command for shutdown 

```
sudo shutdown -h 0
```

---

### Post by haqking on 2011-08-14
> **AndrewBorg said:**
> Hi Guys,

I am encountering a Problem with the TeamSpeak server that I host on my Ubuntu Machine. The Problem I'm having is that when I restart the Computer before Stopping the Service from the Terminal, The Server would encounter an error the next time it is started.

With your help I would like to know if there is a File somewhere that is run when the User want to Reboot or Shutdown the PC, or if I can write a script that runs before Shutting down.

Thanks in Advance

Andrew Borg


[http://www.bigip.co.kr/index.php?document_srl=7420](http://www.bigip.co.kr/index.php?document_srl=7420)

---

