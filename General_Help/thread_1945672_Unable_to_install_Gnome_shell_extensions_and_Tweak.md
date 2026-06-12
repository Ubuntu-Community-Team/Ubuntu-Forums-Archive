---
title: "Unable to install Gnome shell extensions and Tweak tool."
date: 2012-03-23
forum: General Help
---

### Post by BlinkinCat on 2012-03-23
Hi all,

I have been trying to install gnome shell extensions and tweak tool on a fresh install of gnome shell as per these commands - 

[http://ubuntuforums.org/showpost.php?p=11629987&postcount=2](http://ubuntuforums.org/showpost.php?p=11629987&postcount=2)

The following errors are displayed - 
```

sudo apt-get install gnome-shell-extensions-user-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell-extensions-user-theme : Depends: gnome-shell-extensions-common but it is not going to be installed
                                     Recommends: gnome-tweak-tool but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell (>= 3.3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```Can anyone help me solve this problem?

Thank you.

Edit : Decided to try fixing by removal of gnome shell and re-install.
         Only ended up with even more errors on install - have decided to stick with Unity for now.
         Will mark as solved even though I didn't resolve issue.

---

### Post by laserator on 2012-03-29
Bro I have the same problem did you ever figure it out?

---

### Post by kurt18947 on 2012-03-29
> **laserator said:**
> Bro I have the same problem did you ever figure it out?

I don't know if this will help but I don't think it'll hurt.  Install Synaptic if you don't have it then try to install the desired packages assuming they're listed in Synaptic.  Synaptic has fixed dependency problems for me in the past.  I prefer it over Ubuntu Software Center.  Not as pretty Synaptic seems like it can fix things that Software Center may not.

---

### Post by BlinkinCat on 2012-03-30
> **laserator said:**
> Bro I have the same problem did you ever figure it 
out?
Thanks for your input laserator - no I didn't figure it out for sure but I suspect I may have caused an error by not waiting long enough for the first command to complete - I think I may have input some garbage that messed up the commands. I bit the bullet and went for a complete new install and installed gnome shell extensions and tweak tool in exactly the same way as specified in Old Gray Wolf's post and everything was installed correctly this time.

> **kurt18947 said:**
> I don't know if this will help but I don't think it'll hurt.  Install Synaptic if you don't have it then try to install the desired packages assuming they're listed in Synaptic.  Synaptic has fixed dependency problems for me in the past.  I prefer it over Ubuntu Software Center.  Not as pretty Synaptic seems like it can fix things that Software Center may not.
Thanks kurt18947 - Yes I use Synaptic for some things, but thought the commands would work out better in this case - As explained above, all is O.K. now.
I appreciate the input from both of you. 

Cheers -  :-)

---

### Post by laserator on 2012-04-01
I am using Synaptic now. 
According to synaptic I must fix broken packages before I can upgrade  "libgail-3-0" on which another package depends. What is  libgail-3-0? And how can I find out what packages are broken?
thank YOu!

---

### Post by laserator on 2012-04-01
> **BlinkinCat said:**
> 


Thanks kurt18947 - Yes I use Synaptic for some things, but thought the commands would work out better in this case - As explained above, all is O.K. now.
I appreciate the input from both of you. 

Cheers -  :-)
So you did a fresh install? I might do that because according to synaptic I have broken packages. Which is why I cannot install  "libgail-3-0".

---

### Post by kurt18947 on 2012-04-01
> **laserator said:**
> So you did a fresh install? I might do that because according to synaptic I have broken packages. Which is why I cannot install  "libgail-3-0".

This has worked for me, YMMV. In Synaptic I did edit -> fix broken packges.  If the broken packages are fixed,  then run update.  If I just fix broken packages, they won't stay fixed.  I have to run update after.

---

### Post by laserator on 2012-04-02
I fix broken packages then update but when it comes time to install Advanced settings it warns that my packages are broken :(
In the end I just decided to go with dconf, which is probably just as good.
Thanks guys lol.

---

