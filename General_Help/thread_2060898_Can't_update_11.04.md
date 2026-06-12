---
title: "Can't update 11.04"
date: 2012-09-21
forum: General Help
---

### Post by Jilly on 2012-09-21
*Hello i dual boot Windows & Ubuntu 11.04 and the past week i have been trying to do an update, it keeps failing with the message , Failed to fetch HTTP:// security.com , Failed to download package files Check connection, i am connected to the internet.* would anyone have a clue as to why all of a sudden i can't update, be kind i am not a PC wizz:lolflag:

---

### Post by black veils on 2012-09-21
that version of ubuntu has ceased support, so you wont be able to get updates, and you shouldnt be able to download applications either. you need to do a fresh/clean install of ubuntu, or whichever variant. remember to use/install the appropriate desktop environment for your computer hardware.

Edit:

oops, not yet, but it will in october! scroll down to the table [http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29")

you should therefore still do a clean install. there are linux mint options also, which are based on ubuntu.

---

### Post by Karlchen on 2012-09-21
Hello, Jilly,
> **Jilly said:**
> *update, it keeps failing with the message , Failed to fetch HTTP:// security.com*Please, post the content of

[LIST]
[*]the file **/etc/apt/sources.list**
[*]the contents of any ***.list** files in the folder **/etc/apt/sources.list.d**
[/LIST]

If you can reproduce the error message, please, copy and paste it here. Do not post partial quotes from memory.

Kind regards,
Karl

---

### Post by drmrgd on 2012-09-21
Would you mind posting the contents of your sources list?

```
cat /etc/apt/sources.list
```

It may also be helpful to see the full results of the following:

```
sudo apt-get update
```

I'm wondering if there is an issue with one of the repositories in your sources list, as the URL you posted isn't something I'm used to seeing (the normal Ubuntu security repo is [http://security.ubuntu.com](http://security.ubuntu.com)).

Also, for the sake of readability, please use the CODE tags (the little hash marks) when you post those.

---

### Post by Jilly on 2012-09-21
Hello i just realised i missed a word in that message it should read
Failed to download package files 
Check connection 
In the box that was orange , bear with me i don't know a lot 
Failed to fetch
http:// security.ubuntu.com

I actually tried to copy that but i must have done something wrong.
I have read that i can't upgrade if i haven't done the updates for 11.04 is there a way around it or am i better to do what you said Black Veils a clean install as i don't really understand all the technical jargon that you use sorry{self taught pensioner}

---

### Post by black veils on 2012-09-21
on ubuntu site it says > To avoid damaging your running system, upgrading should only be done  from one release to the next release (e.g. Ubuntu 9.04 to Ubuntu 9.10)  or from one LTS release to the next (e.g. Ubuntu 6.06 LTS to Ubuntu 8.04  LTS)you are neither of those, so a fresh install would be best. as the support for your current system is ending in about a week, you should do that.

as for the stuff which confused you:

there are operating systems, ubuntu is one of those. there are others which base themselves on ubuntu, meaning you can use the same applications and most will be the same, except any special themes or applications etc that has been added to the system.

there are desktop environments, unity is one of those (you are possibly using that in ubuntu at the moment). but there are others, like gnome fallback (i forget what it is officially called), gnome shell, xfce, lxde, kde etc. each have different options and tweaks available. some require powerful hardware, like graphics card. which is why i said you should take that into consideration, or bear it in mind if you have bad performance, so you can use another desktop instead, on your installed operating system.

---

### Post by Jilly on 2012-09-21
Thanks very much for your help, i think it will be a clean install but if doing a clean install can i go straight for the newest version?:p

---

### Post by black veils on 2012-09-21
provided your hardware supports it, yes, just make sure not to do any kind of upgrade, and install fresh. there may be an issue with non-pae kernel, if that happens, you can install ubuntu from **mini.iso**, and choose your desktop during the process. 

test the live cd/dvd/usb flash drive in live mode first, by choosing **try** instead of install, and see if it works.

then click the **install** icon to begin the process. before you do that though, it would make things easier if you open the application **gparted**, right-click on the **swap** partition and **swap-off **if necessary. then right-click the **ext3/4** partition and delete it, do the same for **swap**, then click **apply**, when it is finished, close gparted.

you may proceed to the install wizard now and choose** along-side windows**, when given the option of erasing disk or something else for advanced.

---

### Post by Jilly on 2012-09-23
*[B]Thanks very much for all the advice i shall take it onboard and attempt to do a clean install :lolflag:[/B wish me luck):P]*

---

