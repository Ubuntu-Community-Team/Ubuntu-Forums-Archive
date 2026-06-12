---
title: "Installing Adobe Flash Player in Opera"
date: 2010-05-18
forum: General Help
---

### Post by emanuel.b on 2010-05-18
Hi everybody,

Just a little question about installing the Adobe Flash Player. I downloaded the Flash Player library in tar.gz format directly from Adobe. I want to install it in the default plug-in directory for Opera, which is /usr/lib/opera/plugins. When I try to copy the file, I get an error saying that I do not have the sufficient permissions to copy a file to that directory. Does anyone know how to copy the file using the command line, using the SUDO command?

---

### Post by mörgæs on 2010-05-18
Just write sudo in front of the normal command:

```
sudo cp <filename> <to-directory>
```

---

### Post by emanuel.b on 2010-05-18
Thank you very much. That's a command I'll have to remember in the future. :)

---

### Post by mörgæs on 2010-05-19
You are welcome. 

You will find more on the command line (and other useful stuff) in 
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by abclemons on 2010-05-20
@emanuel.b:

I am guessing that the above information solved your question, but I still have a question. Why would you download the tar.gz when you can get the official adobe-flashplugin from the repositories? I know I geek out and use tar.gz's every once in a while, but only if there is no APT or deb available.

I only ask because I have been having issue with flash in Opera and wondered if you stumbled upon this as a solution...

---

### Post by WinterRain on 2010-05-20
> **abclemons said:**
> Why would you download the tar.gz when you can get the official adobe-flashplugin from the repositories?

Because that method doesn't work for opera.

---

### Post by emanuel.b on 2010-05-21
> **abclemons said:**
> @emanuel.b:

I am guessing that the above information solved your question, but I still have a question. Why would you download the tar.gz when you can get the official adobe-flashplugin from the repositories? I know I geek out and use tar.gz's every once in a while, but only if there is no APT or deb available.

I only ask because I have been having issue with flash in Opera and wondered if you stumbled upon this as a solution...

I only do it this way because I enjoy a certain level of control over things. Thats pretty much it. :)

> **WinterRain said:**
> Because that method doesn't work for opera.

Actually WinterRain, it does. Opera looks in the Mozilla plug-ins folder as well as it's own. Since Opera supports the same plug-in architecture as Firefox.

---

