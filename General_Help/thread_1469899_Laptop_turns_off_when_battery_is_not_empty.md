---
title: "Laptop turns off when battery is not empty"
date: 2010-05-02
forum: General Help
---

### Post by Sionek on 2010-05-02
Hello Everyone,

Since I had updated to Lucid, I'm having some trouble with running my laptop on battery. It usually turns off when the battery notifier is still at 13%~18% (it is not shutting down, it is like when your battery runs out of energy). First I had thought that was a problem with the notifier and I was missing when the battery had no charge, but I kept looking at the notifier and suddenly when it had reached 15% my laptop just went down, without saving any job.

I've just upgraded to Lucid Lynx, running on a HP Pavilion dv4-1123us with 2.00 GHz Intel Core2 Duo T5800, 4GB RAM.

The battery is a 6-cell Lithium-Ion that came with the laptop.

I'd bought it about 1 year ago.

This is my first thread in Ubuntu Forums and I also don't have much experience on Linux, so I apologize if there is a lack of information to report this problem and also I thank you if you could help this around.


Thanks in advance!

---

### Post by Sionek on 2010-05-02
Just to add some more info. 

I've turned the laptop on again, with AC plug in, and the battery indicator showed charging with 15% already. Then when it reached 16% I unplugged the AC power and the indicator went down to 6%. I plugged AC again and left it charging to 10%, then unplugged. It went normal and when reached 9% the bubble notification came up showing "Low Critical Battery..."

Could it be a problem with Lucid? It seems more likely that something is wrong with my battery, but it had just started happening when I upgraded to 10.04.

---

### Post by matchu on 2010-05-14
I've been having similar issues.

---

### Post by bluesoldier007 on 2010-05-14
Disclaimer: I am also a beginner Ubuntu user, so this is not a definitive answer.
 
I had a very similar problem on my wife's HP laptop after about 1.5 years.  It was originally running XP, then I "upgraded" to Vista and the laptop just started turning off when there was plenty of battery power left, naturally I suspected the OS change.
 
I did a lot of troubleshooting work on it, starting with re-installing battery driver, and eventually even replaced the battery itself (which still did not work).  I took it in to a repair shop and they determined that it was actually a hardware problem - some of the power regulator hardware was burned out.  The OS change was a complete coincidence.
 
They said that one of the causes for this could have been leaving the laptop plugged in when the power was already full (apparently a common problem for Li-ion batteries, but more often seen in cell phones).  To this day we can't do anything to get the laptop to power on except leave it plugged in so it is working off of the outlet power (but of course it gets very hot because of the burned out hardware).
 
I hope there is a better explanation for your problem.

---

### Post by Sionek on 2010-05-14
Thanks for your reply!

Actually, I think the problem is the battery itself. I booted on Windows 7 and the problems were seen there too. I think it was just a coincidence, the battery started to show some problems very close to the time when I updated from Karmic to Lucid. 
I downloaded a software from HP for Windows (HP Total Care) and it showed that my battery either is too old (not, in this case) or it was broken and should be replaced. After doing this, I went back to Lucid the Update Manager updated my battery package and then it could show the actual battery capacity (about 36%, considering the battery to be replaced too). So, I don't know if it was the package update or the analysis that the HP Total Care did on the battery that made Ubuntu see its capacity.

Besides that, I had not replaced my battery and neither sent the laptop to maintenance. I'm using it most of the time on AC plug. When I get some more info I will post here!

---

