---
title: "Broaband Connection Settings"
date: 2011-04-10
forum: General Help
---

### Post by uditiiita on 2011-04-10
Hello Everyone, ):P

I have just installed Ubuntu 10 and now I want to use BSNL Broadband in ubuntu.
I have tried a lot of options but still not able to configure. so please help me in this problem. :(

Thanks in advance...

---

### Post by dineshs on 2011-04-12
BSNL broadband can be connected in two ways.
1) Modem / router in bridge mode.
If you configure your modem / router in bridge mode you need a PPPoE dialler in your OS . In windows you can make it as explained [here]("http://support.microsoft.com/kb/283070")
The eqiuvalent in ubuntu is [here]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9")
2)Modem / router in PPPoE mode.
In this mode the modem / router is configured with your username and password so that you dont need a dialler.Just open your browser and proceed.The connection will be always ON
Now the questions are 
1)Which method are you using? Do you use a dialler in windows?
2)What is the modelname of your modem?Because Huawei modems are DHCP disabled by default.You may need to set static IP in Network manager.
3)If your ethernet card driver is not OK you may have problems.Open a terminal (applications-accessories-terminal)type the following command and enter ```
sudo lshw -C network
``` Post the result back.Also post the output of```
route -n
```

---

