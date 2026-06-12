---
title: "software center and update manager won't run"
date: 2012-03-24
forum: General Help
---

### Post by Jacob-Gates on 2012-03-24
Hey guys, usually when I have a computer problem I can figure it out for myself but this has me pretty puzzled. I have searched everywhere and tried everything I have read and I am sure there is a reason why they are not working for my specific problem. I am running ubuntu 11.10. When I click the software center in the launcher is blinks then  never opens, also when I try to run the update manager I get a similar message as I get when I run the update command in terminal.

when I do the update command I get this message:

```
E: Type '/ubuntu-wine/ppa/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
E: The list of sources could not be read.

```

I have tried these commands that I found associate with this problem and they did not work:

```
sudo rm -r /var/lib/apt/lists
sudo apt-get update
sudo apt-get update && apt-get upgrade
```

and some others that I do not remember. as for my computer in general everything else seems to be fine. Let me know if you need more information, i tried to give you as much as I thought you needed. Thank you in advance.

---

### Post by jerome1232 on 2012-03-24
looks like line 3 in that file of lists is malformed, lets have a look at what's wrong with it

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```

You can pop it open and edit it like this

```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```

---

### Post by Jacob-Gates on 2012-03-24
here is what is says in both terminal and the text file:

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
/ubuntu-wine/ppa/ubuntu oneiric main # disabled on upgrade to oneiric
```

---

### Post by claracc on 2012-03-24
I think you have to remove from sources.list the third line:

/ubuntu-wine/ppa/ubuntu oneiric main # disabled on upgrade to oneiric

You can edit sources.list (as jerome1232 indicates) in this way from command line: gksu gedit /etc/apt/sources.list and delete the third line.

---

### Post by Jacob-Gates on 2012-03-24
> **claracc said:**
> I think you have to remove from sources.list the third line:

/ubuntu-wine/ppa/ubuntu oneiric main # disabled on upgrade to oneiric

You can edit sources.list (as jerome1232 indicates) in this way from command line: gksu gedit /etc/apt/sources.list and delete the third line.

delete the  entire 3rd line? just making sure before I do it... don't want to royally screw my computer up because of an misunderstanding.

---

### Post by claracc on 2012-03-24
Yes,  the line begining without deb or deb-src :

> Code:
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) oneiric main
[COLOR="Cyan"]/ubuntu-wine/ppa/ubuntu oneiric main # disabled on upgrade to oneiric[/COLOR]




The one marked in blue color

---

### Post by Jacob-Gates on 2012-03-24
Oh my god! that worked! thank you both of you! That was extremely simple. how did the line even get there? any idea? (just to prevent it from happening again, if possible).

---

### Post by jerome1232 on 2012-03-24
Just a side note, when your editing files like this and your worried that something you take away will be detrimental to your system, just comment it out and test, that way if it does break something all you have to do is uncomment to restore it. Believe me this is a very good habit to get into when removing things from system files.

an example of commenting out (you just add a pound sign, some config files will use other symbols on occasion like ";" but you will be able to tell when reading the file if that is the case)

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
[COLOR="blue"]#[/COLOR]/ubuntu-wine/ppa/ubuntu oneiric main # disabled on upgrade to oneiric
```

Once your sure it's working as intended you can delete the line (or just leave it in there commented in case you want know in the future what it is you took out)

---

### Post by claracc on 2012-03-24
The causes can be multiple, it can appeared from editing sources.list manually an accidentally copy  a part of other line or introducing new line , or deleting the # (comment) symbol from the beginning or adding more lines than required when adding ppa to sources list.

There is a more secure way of updating or adding ppas to sources.list through menu:
system ---> administration ---> software sources.

As you have fixed your problem, please mark the thread as solved with the thread tools in the top right of the page

---

