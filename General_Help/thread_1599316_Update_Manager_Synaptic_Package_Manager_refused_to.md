---
title: "Update Manager/ Synaptic Package Manager refused to work"
date: 2010-10-17
forum: General Help
---

### Post by theman1 on 2010-10-17
When i try to open Synaptic Package Manager and update-manager it gives me the following error message:

'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/banshee-team-ppa-maverick.list, E:The list of sources could not be read.'


I appreciate your help on how to solve this error because my system cannot update or install any new application. Thank you so much

---

### Post by ivarn on 2010-10-17
I'm in windows now so sorry if i'm not 100 procent correct here, but go to synaptic and after the error message, go to the edit menu and click Repair Broken Packages.

---

### Post by JackNocturne on 2010-10-17
post the output of the following in terminal command-line

```
cat /etc/apt/sources.list
```

---

### Post by coffeecat on 2010-10-17
Sorry to say this, but neither of the suggestions in posts #2 and #3 will help at all. What we need is the contents of your....

> **theman1 said:**
> /etc/apt/sources.list.d/banshee-team-ppa-maverick.list

... file. This is a PPA and will not be in the /etc/apt/sources.list file.

Go to Places and open a 'Computer' browser window. Double-click on 'filesystem' and then browse to the /etc/apt/sources.list.d/ folder. Double-click on the banshee-team-ppa-maverick.list file and it will open read-only in a text editor. Copy and paste the text into the reply field and enclose this in code tags by using the # icon above the message field.

Then we can see exactly what is wrong with line 2 of that file.

---

### Post by theman1 on 2010-10-18
Here is the text 

# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main
n

---

### Post by yetiman64 on 2010-10-18
<snip> misread the problem, sorry.

---

### Post by yetiman64 on 2010-10-18
Sorry for the double post, but just to let you know, if you have trouble opening Synaptic or updating and a ppa is involved then you can enable/disable the ppas repo at,

System > Administration > Software Sources > Other Software. This allows to update or install etc, but is not a fix for the ppas entry, more a way to work around it.

---

### Post by JackNocturne on 2010-10-18
> **theman1 said:**
> Here is the text 

# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main
n


type in terminal
```
sudo gedit /etc/apt/sources.list.d/banshee-team-ppa-maverick.list
```in the text editor ,remove then "n" at the end of the line, save and exit.

You should be good to update now:)

---

### Post by yetiman64 on 2010-10-18
@ JackNocturne, check the documentation  [--RootSudo--]("https://help.ubuntu.com/community/RootSudo")  in particularly Graphical Sudo down the page a bit for why gksudo should be used with gedit. That is, graphical apps in general should be invoked with gksudo (or gksu).

It probably won't matter in this case, but is a good practice to get into.

btw My old eyes missed that n even when posted directly above me. :) cheers.

---

### Post by JackNocturne on 2010-10-18
> **yetiman64 said:**
> @ JackNocturne, check the documentation  [--RootSudo--]("https://help.ubuntu.com/community/RootSudo")  in particularly Graphical Sudo down the page a bit for why gksudo should be used with gedit. That is, graphical apps in general should be invoked with gksudo (or gksu).



Thanks man, i learn new info too:guitar:

---

### Post by theman1 on 2010-10-18
> **JackNocturne said:**
> type in terminal
```
sudo gedit /etc/apt/sources.list.d/banshee-team-ppa-maverick.list
```in the text editor ,remove then "n" at the end of the line, save and exit.

You should be good to update now:)
Thank you so much. Problem solved.

---

