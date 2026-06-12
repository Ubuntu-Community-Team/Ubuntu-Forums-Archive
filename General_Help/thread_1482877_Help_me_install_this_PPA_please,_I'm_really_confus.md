---
title: "Help me install this PPA please, I'm really confused."
date: 2010-05-14
forum: General Help
---

### Post by chaospoodle on 2010-05-14
**PROBLEM RESOLVED**
[I]
I'm trying to install this PPA to fix a problem that I guess ATI cards have where there's a delay for minimizing, maximizing, etc. windows. I have like a 1.5 second delay for those.

I'm going off: [/I] [I][https://edge.launchpad.net/~bryceharrington/+archive/violet]("https://edge.launchpad.net/%7Ebryceharrington/+archive/violet")

I can do it up until:[/I] [I]
>        **Step 3:** Now, as a one-off, you should tell your  system       to pull down the latest list of software from each archive it  knows       about, including the PPA you just added:     
             sudo apt-get update     
             Now you're ready to start installing software from the PPA!     
I do the update, but then I don't know the name of the package to install it.
What do I type in the prompt after I update. I hate how it just ends there and expects me to know how to install it.
I know you do sudo apt-get install, but I don't know the name of the specific package to install it.

Please help, I'm new to Ubuntu and this is frustrating.[/I] 

**PROBLEM RESOLVED**

---

### Post by devilized on 2010-05-14
the PPA is just a place where you install the package from. Are you looking to install xorg-server? Then I think you'd just do 

```
sudo apt-get install xorg-server
```

---

### Post by chaospoodle on 2010-05-14
I just tried that, said it couldn't find it so that must not be it.

I'm not sure what I'm trying to install besides whatever I need to install from that small tutorial I posted. It doesn't elaborate on how to install it after I update and it just assumes I know what I'm doing, but I'm not.

---

### Post by klemes on 2010-05-14
Try :

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```

This way it will pull out all available upgrades.

---

### Post by chaospoodle on 2010-05-14
Thanks, that fixed installed everything I needed.
Restarted computer and the problem with the delay for maximizing, minimizing, etc is fixed like it said it would.
Problem solved.

Thanks again.

---

