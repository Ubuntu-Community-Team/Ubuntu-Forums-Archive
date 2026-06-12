---
title: "Please help me get the &quot;wobbly window&quot; effect!"
date: 2011-05-26
forum: General Help
---

### Post by KidneyBean on 2011-05-26
With previous installs of Ubuntu, I was able to get the "wobbly window" effect working. In 11.04, I have to go through the compiz config utility. When there, I check "wobby window effect" and lo and behold, nothing happens. In fact, none of the modifications to the compiz config utility work. This is really frustrating. I can't find a solution anywhere. 

The last thing I want to hear though is that it must be my graphics card. If this is your response, please don't even bother. Just leave this thread at once. My graphics card is just fine, thanks.

---

### Post by jim_deadlock on 2011-05-26
ccsm -> Window Management -> Snapping Windows

I think this clashes with wobbly windows, try disabling it if you have it on.

---

### Post by KidneyBean on 2011-05-26
Sorry fella, there's no such thing as "snapping windows" in the CCSM. Anyone else want to give this a shot? I got it working only once then it stopped working. 

Is this one of those issues "too big to handle"?

---

### Post by flipper T on 2011-05-26
see picture

try scrolling

---

### Post by coffeecat on 2011-05-26
> **KidneyBean said:**
> Sorry fella, there's no such thing as "snapping windows" in the CCSM.

Sorry fella, but there is. 

> **KidneyBean said:**
>  Anyone else want to give this a shot?

I was tempted to leave it there because jim_deadlock gave you good advice. However...

1 - You need to disable Snapping Windows before you can enable Wobbly Windows - jim_deadlock was right. You can find Snapping Windows under Window Management in ccsm.

2 - Wobbly Windows works just fine for me in Unity in all the machines (4) I've tested it on.

---

### Post by lightstream on 2011-05-26
ccsm has always warned whenever there's a conflict between two plugins and given the option to disable one or the other of them, has that changed?

Not sure if this could be related, but one thing that took me a while to sort out in Meerkat was that the extra plugins package (compiz-fusion-plugins-extra) had been hidden away and needed to be installed separately. 

It can be done through Software Center by searching for compiz, but you need to click the 'Show 20 Technical Items' link at the bottom in order for this extra package to appear and be selectable.

Once I had it installed, all the juicy compiz goodness I'd come to expect was once more available.

---

### Post by KidneyBean on 2011-05-26
Okay then, let me show YOU what I get in CCSM under "Window Management", mkay?

[IMG]http://i54.tinypic.com/20f2dyp.jpg[/IMG]

---

### Post by KidneyBean on 2011-05-26
Alright, sorry for the rudeness before. But it looks as though I had installed the SIMPLE version of CCSM. I'm now presently downloading the advanced version which should fix up the problem.

Thanks for everyone's help.

---

### Post by KidneyBean on 2011-05-26
NOPE! Problem still not solved. I downloaded the advanced CCSM, still, same as the screen shot I posted. Bizarre, huh? Any help or should I figure this out on my own like I have for every other problem I posted here on the forums?

---

### Post by Je Et on 2011-05-26
If you have on-board graphics and graphics card, like me, you have trouble. People with only one card do not seem to have this problem. Anyway, this worked for me.

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/ ]("http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/")

Hope this helps you out.

---

### Post by VanR on 2011-05-27
Try also installing compiz fusion plugins in synaptic package manager. I also have Snapping Windows in Windows Management. Not sure why you don't have it. Also you did reboot after installing ccsm didn't you?

---

### Post by lightstream on 2011-05-27
Did you make sure that the extra plugins package (compiz-fusion-plugins-extra) has been installed?

The CCSM screenshot you posted isn't just missing Snapping Windows but a whole lot of other stuff. Here's a screenshot of the plug-ins I have available in CCSM after installing the extras package:

[IMG]http://www.kuxas.com/images/compiz-ccsm.jpg[/IMG]

It can be done through Software Center by searching for compiz, but you need to click the 'Show 20 Technical Items' link at the bottom in order for this extra package to appear and be selectable.

---

