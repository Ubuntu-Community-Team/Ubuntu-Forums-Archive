---
title: "Eclipse very slow"
date: 2010-04-24
forum: General Help
---

### Post by HonzaPokorny on 2010-04-24
All I could find on this topic was threads talking about Drapper.

I'm using Karmic and Eclipse is very slow. It's using about 460MB RAM and over heats my laptop. Core due 1.82GHz 2Gb Ram, 64bit.

Anything possibly wrong? Known issues?

Plugins loaded: pydev, cdt, android sdk, hgeclipse

Thanks

---

### Post by WinterWeaver on 2010-04-24
Though eclipse seems to be a great ide, it uses java and naturally extra resources because of that.

Your system however seems that it should handle it fine. are you running the 64bit or 32bit version of Karmic?

---

### Post by john newbuntu on 2010-04-24
In case you have not already tried it, use Sun's version of jre as the underlying vm for eclipse.  I had heard of problems with the default Ubuntu version.  You can find some details here:
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by HonzaPokorny on 2010-04-24
> **WinterWeaver said:**
>  are you running the 64bit or 32bit version of Karmic?

64Bit - it's in the original question.

---

### Post by HonzaPokorny on 2010-04-24
Bump

---

### Post by vibra on 2010-05-24
I have installed eclipse too and I feel the same slowness of eclipse. 

I'm already using Java sun compiler but not seeing improvements at all... :( 

The utilization is slow and tiring...

---

### Post by mthome on 2010-05-24
Not just eclipse, everything is slow and thrashy for me under karmic.

---

### Post by vibra on 2010-05-24
> **mthome said:**
> Not just eclipse, everything is slow and thrashy for me under karmic.

hmm... I should say that I feel Lucid faster than when i used karmic. But in general yah, i have the feeling of slowness in its utilization. But, I don't trust on my HP laptop also (always giving me bad user experiences). 

I miss my Dell laptop running Ubuntu 7.10

---

### Post by HonzaPokorny on 2010-06-06
> **john newbuntu said:**
> In case you have not already tried it, use Sun's version of jre as the underlying vm for eclipse.  I had heard of problems with the default Ubuntu version.  You can find some details here:
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

After much Googling pain, I have managed to set up Eclipse to use the Sun JVM. However, no improvement. The UI still seems very slow. It uses nearly 500MB of RAM. Memory is not really an issues here though - I have 2GB RAM. 

Any other ideas, guys?

---

### Post by vibra on 2010-06-06
Close the projects open in the explorer view. I had 20 projects open, and after i close then (except the one i was working on), the pefomance of eclipse has improved a lot.

---

### Post by BoneKracker on 2010-06-06
I haven't used Eclipse in a while, but I think you may also be able to reduce memory usage by unloading un-needed plugins.

For example, if you're working on C/C++, unload the Python stuff.  As I recall, that's just a matter of un-checking a box or two and restarting it.

In general, though, this seems odd to me, as I have run Eclipse on much less powerful machines.

---

### Post by HonzaPokorny on 2010-06-06
> **BoneKracker said:**
> I haven't used Eclipse in a while, but I think you may also be able to reduce memory usage by unloading un-needed plugins.

Makes no difference. Thanks for the tip, though.

---

### Post by HonzaPokorny on 2010-06-15
Bump.

---

### Post by javarunner on 2010-06-15
Been using Eclipse (myEclipse) on Win platforms for years.  Eclipse on 10.04 doesn't seem any slower/faster than on Win.  However, if you have multiple projects open, it will degrade performance.  I usually have one project open at a time.  Yes, use Sun's JDK although not necessarily for perf reasons.
Have Fun...

---

### Post by sstone53 on 2011-04-14
I have also noticed this and in some cases it is unbareable. however I believe I have found a remedy.

I start eclipse with
nice -n-15
This did not seem to help much.
but once i use ionice it appears to run much much better
ionice -c2 -n0 -p <PID>

---

