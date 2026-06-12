---
title: "Forum Polls"
date: 2011-06-15
forum: General Help
---

### Post by bogjumper on 2011-06-15
Hi

I have been peripheral on Linux for quite a few years and dipped in an out never really getting to grips with it.
I started with DOS 3.3 but as the years wore on became embroiled in Windows. Now at 70 I am again moving towards Ubuntu because it has become much easier to use. I am very appreciative of all the work that has produced such a fine product and use it pretty much exclusively now for emails etc. However like a lot of us old and not so bold anymore I am not mad on change for the sake of change when it leads to confusion.
I started up again with Ubuntu 10 and found it very easy to move around especially into systems etc. Its one drawback was that it was flaky with internet connections. So when 11 came out  I grabbed and  found it 99% better for online work. However the new face that came with it I am unhappy with. It took away all the previous ease and has become a hunt the thimble to find your way around. I appreciate the designers were trying to make it better but I personally feel they have gone wrong and are not looking at the 24 handicap golfer only the pros. The other point is the page slider which you also have to hunt for- a real pain in the back
I am writing this because  I have not been able to find anywhere one can give feedback and hoping that somebody  up there will read. Are Beta versions not put out to ordinary folk or testing and opinion.  I would
like to make a plea that this be considered in the new version. Thanks

---

### Post by jmszr on 2011-06-15
bogjumper,

To set the "Classic Gnome" interface as default: [http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/) or: [http://alexsantidote.com/579/how-to-get-gnome-back-ubuntu-11-04-switch-from-unity-to-classic/](http://alexsantidote.com/579/how-to-get-gnome-back-ubuntu-11-04-switch-from-unity-to-classic/)

To disable the overlay scrollbar (page slider): [http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html) .

I notice that the scrollbar fix requires the use of the terminal; not knowing how well versed you are with the Ubuntu terminal:

To pull up the terminal press Ctrl+Alt+T, then copy and paste into the terminal:

```
sudo su
```

Then press Enter. It will then ask for your password, enter it (it will not be visible [security]) and press Enter.

Next, copy and paste into terminal (and then press Enter):

```
echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars
```

Then:

```
exit
```

Then restart your computer.

That should revert you to the regular style scrollbar, if not:

```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0
```

This will remove the overlay scrollbar package. Details are in the third URL above.

Hope that helps.

The 11.04 release had three Alphas, and two Betas. It has been a somewhat controversial release and Ubuntu is well aware of the objections some have had.

Edit: The terminal is also available under Applications > Accessories > Terminal.

---

### Post by bogjumper on 2011-06-17
Hi JMSZR

Thank you very much for your lucid explanation which I will tackle tomorrow. I hear what you say re Ubuntu paying heed to comments but how does one communicate them. I find most of these larger organisations tend to wrap themselves in a invisible cloak so you can not get to them. I am also a member of the Major Geeks forum and they have a system whereby any answers to your post results in an email calling your attention to which is very useful. Can you direct me to where I can post comments to Ubuntu as I would like to pass on my comments. Strange isnt it Ubuntu is part of the nation around me and yet I am unable to communicate it - togetherness indeed ????

Hamba Gahle

---

