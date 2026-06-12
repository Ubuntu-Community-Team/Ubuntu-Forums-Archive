---
title: "Almost Terminal After Update"
date: 2011-08-01
forum: General Help
---

### Post by mcman56 on 2011-08-01
[COLOR=black][FONT=Verdana]During the latest update, my system locked up. I was able to do a hard restart and complete the update but since that time the system is quite sick. Sometimes it will boot, sometimes not, regardless of weather I use recover mode or earlier versions. Once booted it will run slowly for a while and finally lock up. It always takes a physical power off to get going again. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I sometimes get a message stating "Alimixer1 Creating Error". This seems to come after something related to Firefox and then the system locks.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Are there any suggestions on this?[/FONT][/COLOR]

---

### Post by akoskm on 2011-08-01
> **mcman56 said:**
> [COLOR=black][FONT=Verdana]During the latest update, my system locked up. I was able to do a hard restart and complete the update but since that time the system is quite sick. Sometimes it will boot, sometimes not, regardless of weather I use recover mode or earlier versions. Once booted it will run slowly for a while and finally lock up. It always takes a physical power off to get going again. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I sometimes get a message stating "Alimixer1 Creating Error". This seems to come after something related to Firefox and then the system locks.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Are there any suggestions on this?[/FONT][/COLOR]
I would
```

apt-get update
apt-get check

```
first to make sure that everything on it's place. I'm not sure how recovery mode looks like but if you have desktop manager loaded then switch to a terminal Ctrl+Alt+Fn (n=7 runs the recovery mode so switch to somethings else). Once you are here start
```

top

```
and look for something with extremely CPU or Memory usage.

---

### Post by FormatSeize on 2011-08-01
What is it that you are doing when this is happening? Does your sound work? I did a quick Google search ([link](http://www.google.com/#sclient=psy&hl=en&site=&source=hp&q=Alimixer1+Creating+Error&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=5c88e14de2b269a1&biw=1234&bih=612)) and there seems to be a bug associated with the error message that ou are getting.

---

### Post by AlphaLexman on 2011-08-01
If you have a lot of important data, you should boot from a live CD and back it up if you haven't already!

My first impression is you have a hard disk failing... sectors or blocks or something, however this is just a worse case scenario.

Best case, purge your firefox installation and re-install.

Definitely do a hard disk scan from a live CD. If your drive has SMART capabilities, use the disk utility.

Good Luck!

---

### Post by mcman56 on 2011-08-02
I purged firefox and did the hard disk scan.  The scan seemed to find some issues and I think fixed them.  However, now it does not even get to grub.  I did get a message about welcome to Ubuntu and a root prompt but that was it.
 
Is there a way to reload Ubuntu yet keep my settings?  The only things I really hate to lose are the wireless settings and the wireless printing setup.
 
This is on an older resource limited machine.  If I have to start over, should I use some thing like Xubuntu?  or maybe the same version but reject all of the updates that come through?

---

### Post by amosilan964 on 2011-12-22
Fantastic goods from you, man.
Ive study your stuff ahead of and youre just as well amazing. I enjoy what youve got right here, adore what youre stating and the way you say it. You make it entertaining and you even now manage to help keep it wise. I cant wait to go through additional from you. That is really an incredible .

---

