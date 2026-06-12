---
title: "System-Wide Default Papersize Setting?"
date: 2012-02-07
forum: General Help
---

### Post by 2CV67 on 2012-02-07
I know I should avoid cross-posting, but one of my other threads has brought up a point which should not really be discussed in detail there & which requires this "branching off".

In that thread, I said:
> To Set the System-Wide Default Papersize.

The current method is to navigate to /etc/papersize & rewrite the contents with Admin priviledges & save.
Not that difficult when you know, but hard to find, or find again after a lapse.
The default setting probably depends on something you choose when initially installing Ubuntu, maybe Language?
Doesn't seem to be the more logical "Location", since I always end up with "Letter" here in France where A4 is the only option you will ever need.

Can't think how much time I have wasted trying to reset defaults in OpenOffice & LibreOffice, where I might have expected to be able to do it, only to find my good work over-ruled by some invisible hand.
The invisible hand is /etc/papersize.

To me, the logical place to find a GUI selection of Default Papersize would be in Printer Properties, becoming a Printer-wide, rather than system-wide default.
::::::::::::::::::::::::::::

**mgmiller** replied:
> To Set the System-Wide Default Papersize.

In both 10.04 with gnome 2.x and in 11.10 with unity, the default paper size is set the same way. In printer properties, printer options, General, page size. Whatever is set there will appear in /etc/papersize.

In 10.04/gnome 2.x Click through System > Administration > Printing to bring up the printer driver window. Right click the printer and select properties, printer options, General, page size

In 11.10/Unity, either hit the super key and type printing and click on the icon or in the upper right corner of the top panel, click the power icon and the first choice is system settings. Then click the printing icon. In both cases you will get the same window as 10.04 gave you and it's set the same way.

I often have to change the paper size the first time I use open/libre office also, but it works fine in every other printing application, browsers, etc. Open/Libre Office wants to default to A4 regardless of the default setting in the printer driver properties, but I need US letter. I make that change once, and I'm done.
:::::::::::::::::::::::::::::::

I rechecked as much of that as I could, using 11.10 with Unity 2D & Gnome Classic & Lubuntu (mainly).
As far as I can see:
1. Changing the setting in Printer Options changes what I see in CUPS at localhost:631 but does not change /etc/papersize.
2. Changing /etc/papersize changes the defaults in LibreOffice (my main printing path) but doesn't change what I see in CUPS nor what shows in Printer Options.

I know the LibO situation is very complicated:
[http://ubuntuforums.org/showthread.php?t=1876518](http://ubuntuforums.org/showthread.php?t=1876518)

So now I really would like to know how & where ultimate default papersize should be set.

Thanks for any clarification!

---

### Post by 2CV67 on 2012-02-08
I spent all morning playing with this & it gets worse & worse...

I have a nice fresh install of LTS10.04 as my 'spare wheel' so I looked in there.

Yesterday, I had tried my first printing from that version & found OOo was set to "letter".
I changed /etc/papersize from letter to a4 & OOo displayed & printed as A4.
What I expected.

This morning, to confirm that, I tried changing the 2 parameters I know:
1. /etc/papersize - lets call it PZ.
2. System Tools > Printing > Printer > Printer Properties > Printer Options - lets call it PO.

Now, whatever I put into PZ & PO,  OOo Draw displays the paper on the screen as A4!
Whenever I print, if I look at printer properties, it says A4!
Actually printing, it uses A4.

Back in 11.10 Lubuntu, LibO Draw shows on the screen & prints with whatever I put into PZ & takes no notice at all of PO.

I found these references, which seem to confirm the power of PZ.
[http://manpages.ubuntu.com/manpages/hardy/man8/paperconfig.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/paperconfig.8.html)
[http://taufanlubis.wordpress.com/2007/11/15/how-to-set-all-programs-use-the-same-papersize/](http://taufanlubis.wordpress.com/2007/11/15/how-to-set-all-programs-use-the-same-papersize/)

I think it would be absolutely ideal if PO had real control over the printer's default setting & the reaction of LibO etc to that, as mgmiller says works for him.
How do I get it to work for me?

---

### Post by Khayyam on 2012-02-08
2CV64 ...

/etc/papersize is a global setting. Most (all?) applications should also read the value of the variable "$PAPERSIZE". You can also change the value of the variable "$PAPERCONF" to read a file other than /etc/papersize.

So, if you set the variable in your ~/.bash_profile then there is no need to change the global file ..

```
export PAPERSIZE="a4"
```or to change the file $PAPERCONF uses

```
export PAPERCONF="$HOME/.papersize"
```HTH ...

---

