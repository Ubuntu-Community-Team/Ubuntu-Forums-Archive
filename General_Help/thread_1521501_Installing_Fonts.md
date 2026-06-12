---
title: "Installing Fonts?"
date: 2010-06-30
forum: General Help
---

### Post by Cason on 2010-06-30
So I've just switched to using Ubuntu, and I'm liking it a lot so far. :) I do have a noob-ish question that I can't find an answer to yet in the forums, though.

I'm still in college, and some of my professors are rather picky about the fonts I use in my assignments. Most commonly, I'm required to use Times New Roman for my papers. Is there a way I can install that font so that it can be used in OpenOffice?

I know in Windows installing a font is usually as easy as copying it into the system's font folder. How does one go about installing fonts on Ubuntu?

Thanks!

---

### Post by warfacegod on 2010-06-30
Applications> Accessories> Terminal

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by LMP900 on 2010-06-30
It should come with the ubuntu-restricted-extras package also. If you want other fonts, you can create a folder named *.fonts* within the home folder and drag font files into it. (This is a hidden folder so ctrl-H to reveal it)

---

### Post by warfacegod on 2010-06-30
> **LMP900 said:**
> It should come with the ubuntu-restricted-extras package also. If you want other fonts, you can create a folder named *.fonts* within the home folder and drag font files into it. (This is a hidden folder so ctrl-H to reveal it)

I'm pretty sure that only applies to 10.04. All of the OS's from 9.10 and back have never installed mscorefonts with ubuntu-restricted-extras. I've always needed to install it myself. The 10.04 install I did this morning *did* pull it in with the ubuntu-restricted-extras package.

@cason. You made no statement as to which OS you were using so I didn't want to make an assumption. However, for future reference, most people on this forum *will* make the assumption that you're using the latest "stable" version. That happens to be 10.04 at the moment. You might consider updating your User Profile to reflect which Os it is that you use so that you won't need to state it in any thread you start.

---

### Post by Cason on 2010-07-01
Thanks for your help gentleman!:popcorn:

I'm running 10.04, and as suggested I have changed my profile to indicate as much. I'm downloading the restricted extras pack now, and if that doesn't work, I'll use the terminal command.

Thanks again!

---

### Post by LMP900 on 2010-07-01
> **Cason said:**
> Thanks for your help gentleman!:popcorn:

I'm running 10.04, and as suggested I have changed my profile to indicate as much. I'm downloading the restricted extras pack now, and if that doesn't work, I'll use the terminal command.

Thanks again!

No problem. Hope it installs just fine.

> **warfacegod said:**
> I'm pretty sure that only applies to 10.04. All of the OS's from 9.10 and back have never installed mscorefonts with ubuntu-restricted-extras. I've always needed to install it myself. The 10.04 install I did this morning *did* pull it in with the ubuntu-restricted-extras package.

Are you sure? According to the package details, it was included as far back as [**Hardy**]("http://packages.ubuntu.com/hardy/ubuntu-restricted-extras"). It looks like the package was renamed a year ago, though.

---

### Post by dino99 on 2010-07-01
open synaptic, search "fonts" and make your choice ):P

---

### Post by warfacegod on 2010-07-01
> **LMP900 said:**
> No problem. Hope it installs just fine.



Are you sure? According to the package details, it was included as far back as [**Hardy**]("http://packages.ubuntu.com/hardy/ubuntu-restricted-extras"). It looks like the package was renamed a year ago, though.

Yes. I'm absolutely positive. I've never had access to Arial and such unless I specifically went and got it myself. Not until 10.04 anyway.

---

