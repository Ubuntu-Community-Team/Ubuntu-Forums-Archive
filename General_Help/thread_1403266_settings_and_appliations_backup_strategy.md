---
title: "settings and appliations backup strategy"
date: 2010-02-10
forum: General Help
---

### Post by dln9 on 2010-02-10
I'm not sure if this has been addressed - perhaps there already is a solution out there - I don't know how to look this up.  

Using Ubuntu, there have been many, many times I've had to download many programs/files via Synaptic.  Usually this is in response to some problem I've run into.  I have not been keeping some kind of log of everything I've done.  

I'm thinking, If I ever have to do a fresh install of the same version of Ubuntu, I'm screwed, I'll never remember everything I've downloaded, nor the related options settings I've had to set - I'll end up having to re-figure out a lot of problems all over again.  

Other than a massive, complete system backup, is there some kind of program that logs/tracks this kind of stuff to deal with this potential problem?  Perhaps, at a minimum, something that recognizes everything I've downloaded - at least through Synaptic - that is over and above the base installation?  

Is this making sense?  

Thanks for any help.

---

### Post by jzacsh on 2010-02-10
> **dln9 said:**
> 
Other than a massive, complete system backup, is there some kind of program that logs/tracks this kind of stuff to deal with this potential problem?  
[...]
Is this making sense?  

Thanks for any help.
Yeah, that makes sense. I wouldn't be surprised if there was an attempt at such an application, but I also wouldn't be surprised if there was *no successful* attempts. Software and environment configuration can be a complicated thing, unfortunately.

I think a good place to start, if you don't find any such application, is to learn where config files are conventionally kept and to learn what exactly you care about restoring manually and what you feel **must** be automated.

**At the least** you should know _what_, on your computer, is important to backup. I learned a lot about **what lives where on my pc** just from reading general overviews of [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), which helps you see where configurations you care about (*and don't care about*) are generally stored.

Good Luck.

---

### Post by stinkeye on 2010-02-10
[**_[COLOR="DarkRed"]HowTo: Create a list of installed packages[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=1521615&postcount=1")

---

### Post by rnerwein on 2010-02-10
hi
just a little bit different of what [stinkeye]("http://ubuntuforums.org/member.php?u=684510") do.

i use: dpkg --get-selections | grep -v deinstall > swinstalled.`date +%y.%m.%d-%H:%M`
extract the already uninstalled packetes and a date in my filename. thats because i can fall back to a special date. bdpkg --set-selections < swinstalled.xx.xx.xx.hh.mm
 but stinkeyes way is ok too.
ciao

---

### Post by dln9 on 2010-02-10
Thanks for the replies.  

I'm sorry - I am not yet that familiar with all the commands shown by stinkeye and rnerwein's two methods.  I've looked around on Google to try to deduce what the commands mean, but I fear I'm just getting confused.  Could one you briefly walk me through what each command line does in the two options each of you have shown?  I just want to understand exactly what is happening when I execute each command.

---

### Post by jzacsh on 2010-02-11
> **dln9 said:**
>  I just want to understand exactly what is happening when I execute each command.

Totally understandable.

> **dln9 said:**
> I'm sorry - I am not yet that familiar with all the commands shown by stinkeye and rnerwein's two methods.  I've looked around on Google to try to deduce what the commands mean, but I fear I'm just getting confused.  Could one you briefly walk me through what each command line does in the two options each of you have shown? 

Could you list each command that confuses you? More importantly, before trying google have you tried the man pages? or --help? eg.:
```
man dpkg
```

If what I just asked sounds like gibberish, you may want to take a look at:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by dln9 on 2010-02-12
Thanks for the tips.  

I looked at the man stuff.  But, I'm still not understanding this.  

merwein wrote this command:  


dpkg --get-selections | grep -v deinstall > swinstalled


From the man pages I think this is saying to get all the packages installed, and then find the word "deinstall" in them, and print out the version of grep (I don't know why that matters), and print the version of grep in a file called "swinstalled".  The man pages don't explain to me the significance of finding the word "deinstall" in the packages selected.  I don't know what it means that the word "deinstall" exists somewhere in the selected packages, and therefore why it is useful in his command.  How does that help him track the applications that have been installed (the point of my original question)?  

Did I miss something in these man pages that would have explained this to me?  

Thanks for any further help.

---

### Post by IcarusR on 2010-02-12
```
grep -v
``` = invert match

So command means.. 

get list of packages, grep invert match to deinstall & write it to file swinstalled

---

