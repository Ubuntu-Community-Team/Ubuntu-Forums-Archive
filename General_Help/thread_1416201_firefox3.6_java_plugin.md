---
title: "firefox3.6 java plugin"
date: 2010-02-25
forum: General Help
---

### Post by luofeiyu on 2010-02-25
my system:
ubuntu9.1+firefox3.6+jre1.0.6_18
there is a problem:
i can't use java plugin,how can i do?
i can't open  the web:
[https://www.ppshk.com/hkt/revamp2/English/LoginPage.html](https://www.ppshk.com/hkt/revamp2/English/LoginPage.html)
(open [http://www.ppshk.com/index_c.html,then](http://www.ppshk.com/index_c.html,then) click login to see if you can 
login,in windowxp i can login,plese make a try with your ubuntu,then you can understand what i say)

---

### Post by mikewhatever on 2010-02-25
Can you post the output of <ls ~.mizilla/plugins>. Since you seem to have installed java manually, I suspect the plugin is missing.

---

### Post by wojox on 2010-02-25
[Install JAVA]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Get-JRE")

---

### Post by luofeiyu on 2010-02-25
i have use some command,it's no use .
pt@pt-laptop:~$ sudo ln -vs /home/pt/jre1.6.0_18/plugins/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
`/usr/lib/firefox/plugins/libjavaplugin_oji.so' -> `/home/pt/jre1.6.0_18/plugins/i386/ns7/libjavaplugin_oji.so'
pt@pt-laptop:~$ sudo ln -vs /home/pt/jre1.6.0_18/plugins/i386/ns7-gcc29/libjavaplugin_oji.so /usr/lib/firefox/plugins
ln: creating symbolic link `/usr/lib/firefox/plugins/libjavaplugin_oji.so': File exists
here is my java install(attachment),

---

### Post by luofeiyu on 2010-02-25
hai everybody,please to make a try ,can you  longin   with ubuntu?
[https://www.ppshk.com/hkt/revamp2/En...LoginPage.html](https://www.ppshk.com/hkt/revamp2/En...LoginPage.html)
(open [http://www.ppshk.com/index_c.html,then](http://www.ppshk.com/index_c.html,then)  click login to see if you can)

---

### Post by scouser73 on 2010-02-25
> **wojox said:**
> [Install JAVA]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Get-JRE")

+1 for this site

---

### Post by mikewhatever on 2010-02-26
> **luofeiyu said:**
> i have use some command,it's no use .
pt@pt-laptop:~$ sudo ln -vs /home/pt/jre1.6.0_18/plugins/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins
`/usr/lib/firefox/plugins/libjavaplugin_oji.so' -> `/home/pt/jre1.6.0_18/plugins/i386/ns7/libjavaplugin_oji.so'
pt@pt-laptop:~$ sudo ln -vs /home/pt/jre1.6.0_18/plugins/i386/ns7-gcc29/libjavaplugin_oji.so /usr/lib/firefox/plugins
ln: creating symbolic link `/usr/lib/firefox/plugins/libjavaplugin_oji.so': File exists
here is my java install(attachment),

You are using the wrong path, in fact, the one that doesn't exist by default. [s]/usr/lib/firefox/*[/s]

---

### Post by luofeiyu on 2010-02-26
how can  i  do?
dear mikewhatever,please ask me a question can you login that web or not?

---

### Post by luofeiyu on 2010-02-26
sudo find / -name '*firefox*' 
here is the output:
/usr/lib/firefox-3.6
/usr/lib/firefox-3.6/firefox.sh
/usr/lib/firefox-3.6/firefox-bin
/usr/lib/firefox-3.6/firefox-restart-required.update-notifier
/usr/lib/firefox-3.6/firefox
/usr/lib/firefox-3.6/firefox-
/usr/lib/firefox-3.6/defaults/pref/firefox-branding.js
/usr/lib/firefox-3.6/defaults/pref/firefox.js
/usr/lib/firefox-3.6/defaults/pref/firefox-l10n.js
/usr/lib/firefox
/usr/lib/firefox-addons

---

### Post by mikewhatever on 2010-02-26
> **luofeiyu said:**
> how can  i  do?
dear mikewhatever,please ask me a question can you login that web or not?

I don't have Java installed, so no, I can't login. You should follow the above linked guide and create the plugin for Firefox3.6 properly.

```
For Firefox 3.6 and newer:
ln -s /opt/java/32/jre1.6.0_18/lib/i386/libnpjp2.so ~/.mozilla/plugins/


```

---

### Post by luofeiyu on 2010-02-26
i install  myjre in the /home/pt/jre1.6.0_18,and mozilla  installed in the 
/usr/lib/mozilla, so here is my command:
sudo ln -s   /home/pt/jre1.6.0_18/lib/i386/libnpjp2.so   /usr/lib/mozilla/plugins/
after restart ,problem is solved ,think  you ,mikewhatever.

---

