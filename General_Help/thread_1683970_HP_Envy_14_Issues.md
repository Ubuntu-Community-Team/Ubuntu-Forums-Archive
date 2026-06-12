---
title: "HP Envy 14 Issues"
date: 2011-02-08
forum: General Help
---

### Post by calc0000 on 2011-02-08
Hi all,

I own an HP Envy 14 ([http://www.amazon.com/gp/product/B0042EKEK6/ref=oss_product](http://www.amazon.com/gp/product/B0042EKEK6/ref=oss_product)).  Letting Ubuntu (or any Linux) attempt to boot into a Live CD without changing any parameters results in a black screen, but with everything else working (for Ubuntu, that means the login sound is played).  I've discovered that putting nomodeset in the kernel line will allow me to get so far as a command line, but I can't startx from here (I get "Screen(s) found, but none have a usable configuration.").  I think my issues have something to do with the dual/switchable graphics in my laptop.

I would very much appreciate any advice on getting Ubuntu to boot successfully.

--EWF

---

### Post by dcstar on 2011-02-09
> **calc0000 said:**
> Hi all,

I own an HP Envy 14 ([http://www.amazon.com/gp/product/B0042EKEK6/ref=oss_product](http://www.amazon.com/gp/product/B0042EKEK6/ref=oss_product)).  Letting Ubuntu (or any Linux) attempt to boot into a Live CD without changing any parameters results in a black screen, but with everything else working (for Ubuntu, that means the login sound is played).  I've discovered that putting nomodeset in the kernel line will allow me to get so far as a command line, but I can't startx from here (I get "Screen(s) found, but none have a usable configuration.").  I think my issues have something to do with the dual/switchable graphics in my laptop.

I would very much appreciate any advice on getting Ubuntu to boot successfully.

--EWF

Try the Ubuntu Netbook distro.

---

### Post by calc0000 on 2011-02-10
> **dcstar said:**
> Try the Ubuntu Netbook distro.

Wow, that works.  2 questions: why does it work, and will there be any issues if I install it?

Edit:  I tried to boot into it again, and I'm having the same issue.  Wut?

---

### Post by calc0000 on 2011-02-11
Update:

I've discovered that if I boot into Windows, set the graphics card to Intel, then force shutdown the laptop, I can boot into Ubuntu Netbook.  So it seems that the issue is the computer defaults to the ATI adapter on boot, and this just doesn't work.  So is there a way to make it default to the Intel adapter, or have Ubuntu switch it on boot if I were to install to my hard drive?

Also, I would appreciate it if a mod could move this thread to the laptop section (I think this is the wrong one).

--EWF

---

### Post by calc0000 on 2011-02-15
Bumpity.

Any advice?  I don't mind using just the Intel adapter; I don't plan to do any 3D stuff.

---

### Post by afoglia on 2011-02-17
I assume you are running maverick.  I was running maverick until I upgraded to natty.  (I don't suggest it.  The graphics are much less stable on natty.  Bad enough I'm thinking of downgrading.)

I have no idea what your problem is though.  My Envy 14 has always used the integrated graphics on boot.  There is a common problem though where the screen will start with minimum brightness. [This post]("http://ubuntuforums.org/showpost.php?p=10117053&postcount=13") has a solution to that.

You should be able add other lines to rc.local to ensure the desired card is on.  There is a switch_between_cards.sh script floating around (google for it), but it's unfortunately designed to be run from a GUI.  (I'd like to factor out the logic to a command-line script for precisely this purpose, but I haven't had time.  I'll try to push it to the top of my queue.)

---

### Post by t3h_pwnage on 2011-04-13
I have the same problem with Envy 14. When I startx it says screens found without usable configuration.

When I popped the Linux USB boot in my mom's laptop and typed startx it started without a problem, so it's definitely not the fault of the USB boot.

Would appreciate if anyone found solutions to this :/

---

### Post by t3h_pwnage on 2011-04-14
Ok I found how to fix this. In the beginning type  fixvesa  Then type  startx  It should work now :)

---

