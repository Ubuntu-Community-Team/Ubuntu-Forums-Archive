---
title: "Sensors Screenlet shows one extra CPU core"
date: 2009-10-22
forum: General Help
---

### Post by wolfganggold on 2009-10-22
Whenever I run the Sensors Screenlet, it allows me to show CPU utilization for one more core than I have, on multiple machines.  On a single core laptop, it lets me monitor CPU0 and CPU1.  On my dual core machine at home and also (different manufacturer) dual core machines here at work, it allows me to monitor CPU0, CPU1, and CPU2.  The output appears to be different for each one.  Any ideas as to what is going on there?

---

### Post by Giblet5 on 2009-10-22
Off-by-one error in the code, probably.

It's just a script, and an easy one at that. Fix it or ask the maintainer to fix it. The maintainer is probably listed in the comments at the top of the script.

---

### Post by StuartN on 2009-10-22
> **Giblet5 said:**
> Fix it or ask the maintainer

This seems to be an impolitely abrupt response to a legitimate question.

[QUOTE=]The Code of Conduct is credited with setting the tone of the Ubuntu community and making it welcoming and comfortable to newbies who were turned off by other elitist, RTFM-happy distribution communities that were sadly common. It is the code that drew me in to the Ubuntu community.[/QUOTE] [http://www.geekosophical.net/?p=343](http://www.geekosophical.net/?p=343)

---

### Post by wolfganggold on 2009-10-22
heheh, I have a pretty thick skin :)  

I looked in /usr/share/screenlets/Sensors/SensorsScreenlet.py and can sort of tell what's going on but I'd probably screw it up if I just went in there and started changing things willy-nilly.

One thing I've noticed is that in some apps, such as System Monitor, the cores are listed as CPU1 and CPU2 but if I run the Sidebar screenlet, which shows CPU utilization but doesn't let you specify which cores to display, it shows them as CPU0 and CPU1.

It's really not a huge deal but certainly a curiosity.

---

### Post by Giblet5 on 2009-10-22
> **StuartN said:**
> This seems to be an impolitely abrupt response to a legitimate question.

Terse, which my comment was, and impolite, which my post was not, are not the same things. There are no forum guidelines that describe the level of terseness that is appropriate/inappropriate. If there were such a guideline then only the incompetent would volunteer help here, and without competent help, Ubuntu would be significantly less.

The OP didn't complain and they got the most accurate answer, quickly. Your in-thread criticism of others hasn't helped anyone save perhaps your fragile ego.

If you disagree, this is best taken offline where it should have been to start with.

---

### Post by Giblet5 on 2009-10-22
> **wolfganggold said:**
> heheh, I have a pretty thick skin :)

I looked in /usr/share/screenlets/Sensors/SensorsScreenlet.py and can sort of tell what's going on but I'd probably screw it up if I just went in there and started changing things willy-nilly.

One thing I've noticed is that in some apps, such as System Monitor, the cores are listed as CPU1 and CPU2 but if I run the Sidebar screenlet, which shows CPU utilization but doesn't let you specify which cores to display, it shows them as CPU0 and CPU1.

It's really not a huge deal but certainly a curiosity.


I wasted time responding to the thread's self-appointed feelings and happiness monitor because I'm not rushed now. Here's the less-terse answer:

This has to do with physical v logical numbering schemes, device enumeration, and package maintainers.

To the average Joe, three objects can be numbered 1, 2, and 3.

To a programmer, they'd be numbered 0, 1, and 2. This is related to array offsets (array + 0 offset = first element, array + 1 offset = second element, ...)

To the package maintainer, he's not sure what it should be but has to make a guess and that 0, 1, 2 thing looks weird so he adds another one so that there can be an object named 3. There are three objects so one of 'em has to be a 3, right?

Whoops. He made an mistake.

It's the same thing with the sensors screenlet.

The maintainer should be listed at the top of the script.

---

### Post by jm2003uk on 2009-10-22
Hmm....not sure how related this is, but i have a similar thing happening. When i look in the System Monitor, i have two processors listed (CPU0 and CPU1) though i'm using a netbook with the Intel Atom N270 processor.....which is only single core.

Like the OP, this doesn't really bother me....it's just a bit odd. Everything else is detected and listed corrently.

---

### Post by John Bean on 2009-10-22
> **StuartN said:**
> This seems to be an impolitely abrupt response to a legitimate question.[]("http://www.geekosophical.net/?p=343")
Your intervention is a bit like the Toes Clause - but in reverse ;-)

---

### Post by falconindy on 2009-10-22
Shot in the dark -- maybe its related. Conky provides the ability to monitor cpuN, where N can be 0 through the number of processors you have. If you specify 0, it gives you an average of all the cores. Any number above 0 will give you specific activity for that particular core.

---

### Post by wolfganggold on 2009-10-22
@ jm2003uk:  why did I think that the Atom WAS dual core?  A bit of cranial flatulence I guess :)  

@ StuartN:  I was not familiar with the Toes of Conduct...I like it!

@ Giblet5:  I don't mind terseness one single bit.  I appreciate your help!

So, when looking at that python script, I AM looking in the right place, correct?  There's an email address at the top...I might send him a message to get some clarification.  If it's a mistake it oughta be fixed, seeing as this screenlet is part of the default package.  If it's NOT a mistake, I might learn something anyway!

---

### Post by Giblet5 on 2009-10-22
> **jm2003uk said:**
> Hmm....not sure how related this is, but i have a similar thing happening. When i look in the System Monitor, i have two processors listed (CPU0 and CPU1) though i'm using a netbook with the Intel Atom N270 processor.....which is only single core.

Like the OP, this doesn't really bother me....it's just a bit odd. Everything else is detected and listed corrently.

I'm not sure how closely System Monitor probes to identify the Atom processor family. It may think all Atom cpus are in the 300 series. From user (non-kernel) space, there may have been no way to reliably tell the 200 from the 300 when the System Monitor code was last updated.

Keeping up with hardware changes is tough work.

The desktop monitoring gadgets will never keep up with the advances in technology. That's a good thing. :)

---

### Post by Giblet5 on 2009-10-22
> **wolfganggold said:**
> @ jm2003uk:  why did I think that the Atom WAS dual core?  A bit of cranial flatulence I guess :)  

@ StuartN:  I was not familiar with the Toes of Conduct...I like it!

@ Giblet5:  I don't mind terseness one single bit.  I appreciate your help!

So, when looking at that python script, I AM looking in the right place, correct?  There's an email address at the top...I might send him a message to get some clarification.  If it's a mistake it oughta be fixed, seeing as this screenlet is part of the default package.  If it's NOT a mistake, I might learn something anyway!

Yeah. That's the place to look and that's the guy to ask.

Screenlets are clever and fairly easy. Write a [ClearSky]("http://cleardarksky.com/csk/") screenlet and I'll contribute via paypal. I want one and don't have time.

---

### Post by wolfganggold on 2009-10-22
> Write a ClearSky screenlet 

That's a GREAT idea!  I love the ClearSky Clock!  Are you a fellow amateur astronomer?

---

### Post by Giblet5 on 2009-10-22
> **wolfganggold said:**
> That's a GREAT idea!  I love the ClearSky Clock!  Are you a fellow amateur astronomer?

Yep. I even live in a blackout area (no light pollution by law).

8" Celestron SC with their EQ tripod's tracking rig mounted to snap onto a cement pier on the hill. Gig-E and 115V AC to the pier. I can sit in my cozy living room and control everything (heaters, guidance, etc) right from my PC. :)

---

### Post by wolfganggold on 2009-10-22
Nice!  My best observation point is about 90 minutes from here.  Need to schedule a night up there soon actually.

What a great setup!  Do you run a Mallincam or some such?

My stuff is a bit more modest but it does the job...an 8" Orion Dob that I've upgraded a bit with a moonlight focuser, Bob's Knobs, A Rigel Quickfinder and a fully flocked tube.  I want Orion's new 14" Truss Dob!

---

