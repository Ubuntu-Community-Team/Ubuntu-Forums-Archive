---
title: "help with broken packages"
date: 2009-12-18
forum: General Help
---

### Post by domedmunds on 2009-12-18
I am trying to share a folder on my machine, when trying to do this it asks me to install the services, i've tried to do this but it then tells me that their are broken packages which need to be fixed.

i've had a look in the synaptic manager but nothing is coming up as broken.

i'm kind of at a loss at what to do now. can anyone help or offer a suggestion on where i may look?

---

### Post by ubudog on 2009-12-18
Open a terminal and type ```
sudo dmsg --configure
```

---

### Post by domedmunds on 2009-12-18
> **ubudog said:**
> Open a terminal and type ```
sudo dmsg --configure
```
that returns 'command not found'

---

### Post by pbrane on 2009-12-18
Just in case, try looking at this page:
[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages")

Or this one:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124")
Look at post #9

---

### Post by ubudog on 2009-12-18
> **domedmunds said:**
> that returns 'command not found'

Yes, I am sorry.  I meant "dmesg", so ```
sudo dmesg --configure
```

---

### Post by joes7 on 2009-12-18
> **ubudog said:**
> Yes, I am sorry.  I meant "dmesg", so ```
sudo dmesg --configure
```
Yes, dmseg, infact :)! Don't worry, we all make mistakes. I am making one right now.

---

### Post by ubudog on 2009-12-18
I am so stupid..... I meant dpkg......haven't slept for a while.  So, finally: ```
sudo dpkg --configure
```

---

### Post by domedmunds on 2009-12-19
cheers ubodog, however we are now being returned:

dpkg: --configure needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

---

### Post by domedmunds on 2009-12-19
thank you pbrane. I have been through these posts prior to appealing to you all :) i am new at this, and have been carefully copying commands but it leaves me a little stumped ;)

---

### Post by Soul-Sing on 2009-12-19
> **ubudog said:**
> I am so stupid..... I meant dpkg......haven't slept for a while.  So, finally: ```
sudo dpkg --configure
```

```
dpkg --configure -a
```

---

### Post by domedmunds on 2009-12-19
thanks leoquant, should this command return a result? could you give me an idea of it's purpose. thanks for bearing with a newbie.

d

---

### Post by ubudog on 2009-12-19
> **domedmunds said:**
> thanks leoquant, should this command return a result? could you give me an idea of it's purpose. thanks for bearing with a newbie.

d

I don't know if it should return a result, but it should fix it.  This may help explain to you what dpkg does.  [http://en.wikipedia.org/wiki/Dpkg]("http://en.wikipedia.org/wiki/Dpkg")

---

### Post by domedmunds on 2009-12-20
unfortunately the last command:

[FONT="Courier New"]dpkg --configure -a
[/FONT]
did'nt appear to remedy my problem as it is still telling me there is a broken package.

---

### Post by Leppie on 2009-12-20
Go to Systen>Administration>Synaptic, then click the "Custom Filters" button in the bottom left panel, then select the "Broken" section in the upper left panel and reinstall or remove the packages.

---

### Post by domedmunds on 2009-12-20
Hi Leppie, I had initially looked at this but it is'nt showing any packages as being broken. nothing in the list.

---

### Post by Leppie on 2009-12-20
> **domedmunds said:**
> Hi Leppie, I had initially looked at this but it is'nt showing any packages as being broken. nothing in the list.

what is the exact message you are getting?

---

### Post by domedmunds on 2009-12-20
leppie, a window appears with a red warning symbol and the message

'Could not apply the changes! Fix broken packages first.'

As mentioned in an earlier post I am trying to share a folder. When selecting the option an alert window appears stating

'Sharing service is not installed. You need to install the windows networks sharing service in order to share your folders.'

I then click install and the error message about broken packages comes into play.

---

### Post by Soul-Sing on 2009-12-20
domedmunds which version of ubuntu do you use at the moment?

---

### Post by domedmunds on 2009-12-20
currently running 9.10 on an eee pc 1008HA.

---

### Post by kontara on 2011-06-27
Notice that there has not been an answer to this inquiry.  But I have the exact same problem right now with Lucid 10.04.2 on a Dell Mini 1010.  Anyone solved this one yet?

Thanks.

---

