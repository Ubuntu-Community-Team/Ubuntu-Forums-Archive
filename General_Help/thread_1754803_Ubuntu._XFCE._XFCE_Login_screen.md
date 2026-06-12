---
title: "Ubuntu. XFCE. XFCE Login screen?"
date: 2011-05-10
forum: General Help
---

### Post by Roasted on 2011-05-10
I'm running Ubuntu 11.04 on my laptop. At work, we are beginning to tinker with running Ubuntu on our student systems (school district). The thing is, Unity and Gnome Shell are new enough that they are not considered right now as viable options to test in. That said, an alternative was needed that was quick on older systems yet very configurable. Bam. XFCE.

So I installed XFCE on my Ubuntu machine. This way I can tinker with the interface as if I was a student but then I can bounce back to Unity which I do prefer for personal use. The thing is, the login screen switches over to XFCE's. Is there a way to get my regular Ubuntu login screen back?

---

### Post by BlouBlou on 2011-05-10
You have to set by default to use GDM (It's what Ubuntu uses).

---

### Post by Roasted on 2011-05-10
> **BlouBlou said:**
> You have to set by default to use GDM (It's what Ubuntu uses).

That's what I thought, but I don't see anything at the login screen to select it. How is it done now?

I also tried:

sudo dpkg-reconfigure gdm 

but it returned nothing in terminal.

---

### Post by The Cog on 2011-05-10
Having clicked on your username at the login screen, you then see a pasword prompt. Is there a choice of session type at the bottom of that screen? Just a guess.

---

### Post by Roasted on 2011-05-10
> **The Cog said:**
> Having clicked on your username at the login screen, you then see a pasword prompt. Is there a choice of session type at the bottom of that screen? Just a guess.

Session type? Yes. That's how I switch from Unity to Unity 2D and XFCE.

The thing is, my splash screen is Xubuntu. My login screen is Xubuntu. And now that I have Xubuntu installed, Ubuntu Unity logs in with the Xubuntu theme.

I want Ubuntu 11.04 in its entirety just left alone. I want it 100% like it was, but I want XFCE as a viable option.

I remember this when I installed Kubuntu-Desktop on Ubuntu. What a mistake that was...

---

### Post by sisco311 on 2011-05-10
> **Roasted said:**
> 
The thing is, my splash screen is Xubuntu. 


```

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```

> **Roasted said:**
> 
My login screen is Xubuntu.

Remove the xubuntu-gdm-theme package:
```
sudo apt-get purge xubuntu-gdm-theme
```

---

### Post by Roasted on 2011-05-11
All I ran was this command that sisco311 suggested above:

sudo apt-get purge xubuntu-gdm-theme

And it was fixed.

Thanks!

---

