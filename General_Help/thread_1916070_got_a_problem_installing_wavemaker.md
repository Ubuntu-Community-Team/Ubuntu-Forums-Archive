---
title: "got a problem installing wavemaker"
date: 2012-01-27
forum: General Help
---

### Post by the great sayaman on 2012-01-27
i currently have ubuntu 11.10 on my laptop whose specs are: core i5, with 2 GB ram

i am trying to install wavemaker but there is a big problem that the thing 

JUST WILL NOT INSTALL

i downloaded the .deb package and tried to install it but the damn thing just will not install 

at first i tried to double click it and open it directly but then the software center opened and began to redownload it i let it redownload and when it said fully installed i checked and it was no where to be found.

i then found this site:

[http://www.nielmalan.com/2011/02/wavemaker-install-ubuntu-10-04/]("http://www.nielmalan.com/2011/02/wavemaker-install-ubuntu-10-04/")

I have already replaced open jdk with sun jdk as it said in the comments and then i did everything that it said but in the end it said to add this:

```
./opt/wavemaker-community-6.X.XGA/bin/wavemaker.sh start
```

to  /etc/rc.local

the tutorial is for ubuntu 10.04 so im not sure whether the code should be different for ubuntu 11.10 and im not sure what that code will do and whether it is safe to add that to the directory or not could someone please tell me whether the code is safe and what exactly it will do???

---

### Post by wolfen69 on 2012-01-27
Unless someone else has used this app, it may be difficult to get a straight answer. However, I think it should be safe to try that command. If something did happen, you could always just remove the file and look for other options.

---

### Post by the great sayaman on 2012-01-27
i did it and i go this as a reply:

```
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```


What do i do now???

---

### Post by satanselbow on 2012-01-27
As luck would have it Mr Wolfen ;)

1st time it runs it needs admin priv to set up config and install addons. Try this in a terminal:


```
sudo /opt/wavemaker-6.4.4GA/bin/wavemaker.sh start
```

If that does not work try

```
whereis wavemaker.sh
```

and substitute the path you get back in the one above ;)

Just had a look at the link you posted - I don't do the rc.local startup and prefer to create a .desktop file so I can start it as required :popcorn: It will also then appear in your app menu which is not something the default installer provides :(

---

### Post by the great sayaman on 2012-01-27
> **satanselbow said:**
> As luck would have it Mr Wolfen ;)

1st time it runs it needs admin priv to set up config and install addons. Try this in a terminal:


```
sudo /opt/wavemaker-6.4.4GA/bin/wavemaker.sh start
```

If that does not work try

```
whereis wavemaker.sh
```

and substitute the path you get back in the one above ;)

Just had a look at the link you posted - I don't do the rc.local startup and prefer to create a .desktop file so I can start it as required :popcorn: It will also then appear in your app menu which is not something the default installer provides :(


thank you it worked have been on this since morning and finally did it with your help :D

a thousand thanks my friend

BUT could you please tell in more detail how to get that to the app menu i have no idea of what im doing i was just blindly following the tutorial

---

