---
title: "Trouble Installing Banshee"
date: 2012-02-22
forum: General Help
---

### Post by giodamelio on 2012-02-22
I have used Banshee for awhile and it has worked great. Then just the other day it stopped working. I was going to reinstall it so I ran "sudo apt-get purge banshee". Then when I try to reinstall it, I get a huge error.

I put the whole thing here
[http://pastebin.com/09imNvZq]("http://pastebin.com/09imNvZq")

I think the key is this.
```
* Installing 8 assemblies from libboo2.0.9-cil into Mono
sh: /usr/bin/mono: not found
```
I can't figure out why the mono binary is not there...
Just in case it helps, the output of "where mono" is
```
/usr/local/bin/mono
/usr/local/bin/mono
```

Any help would be greatly appreciated.

---

### Post by IWantFroyo on 2012-02-22
Try running
```
sudo apt-get install -f
```

It should fix the dependencies.

---

### Post by giodamelio on 2012-02-22
I tried that, it gave me the same error.

---

### Post by LinuxFan999 on 2012-02-22
I would recommend removing Banshee and installing a different music player, like Rythmbox.

---

### Post by giodamelio on 2012-02-22
The only program that have gotten to work with my iPod Touch is banshee.

After a quick web search I tried to install amarok, It turns out that error happens whenever I try to use apt-get install.

---

### Post by IWantFroyo on 2012-02-22
```
sudo apt-get update
```

If worst comes to worst, I would try changing the repositories. (Software Center->Edit->Sources in Oneiric).

---

### Post by giodamelio on 2012-02-22
What do you mean by change the repositories? You mean the server I download them from?

---

### Post by IWantFroyo on 2012-02-22
Yes. In Lucid there's a program called "Software Sources," although this was absorbed into the Ubuntu Software Center for Oneiric.
On the opening tab there's a place where you can change to other repositories within the area. Ubuntu's servers are incredibly slow with updates and such. This is the first thing I do after installing.

---

### Post by giodamelio on 2012-02-22
I changes my source and tried apt-get update. Still nothing.

---

### Post by directhex on 2012-02-23
> **giodamelio said:**
> I have used Banshee for awhile and it has worked great. Then just the other day it stopped working. I was going to reinstall it so I ran "sudo apt-get purge banshee". Then when I try to reinstall it, I get a huge error.

I put the whole thing here
[http://pastebin.com/09imNvZq]("http://pastebin.com/09imNvZq")

I think the key is this.
```
* Installing 8 assemblies from libboo2.0.9-cil into Mono
sh: /usr/bin/mono: not found
```
I can't figure out why the mono binary is not there...
Just in case it helps, the output of "where mono" is
```
/usr/local/bin/mono
/usr/local/bin/mono
```

Any help would be greatly appreciated.

It seems for some reason your Mono isn't installed? And you have some self-compiled version?

What does "dpkg -l mono-runtime" say?

---

