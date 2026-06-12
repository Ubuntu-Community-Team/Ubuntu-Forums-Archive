---
title: "Matlab crashes thunderbird"
date: 2009-07-27
forum: General Help
---

### Post by Warthaug on 2009-07-27
I am having an unusual problem and cannot figure out what the problem is.

I am running Ubuntu 9.04, thunderbird  2.0.0.22 and matlab 2008b.  Thunderbird runs fine on its own, as does matlab.  But for some reason, if I'm running both thunderbird gets shut down (as in it disappears from the desktop, and it disappears as a process as well).  If I try to re-start thunderbird one of two things happen - either the splash screen appears and then disappears without thunderbird itself loading, or thunderbird loads normally but disappears again a few seconds later.

Even odder, I cannot re-start thunderbird even after I shut down matlab - I have to completely reboot to get thunderbird to run.

Matlab runs normally, regardless of whether thunderbird is loaded or not.  Thunderbird runs fine so long as matlab isn't loaded.  Also, matlab does not seem to interfere with the running of any other programs - off the top of my head, I've run openoffice, imagej (java), firefox, calculator, text editor, totem, transmission, boinc and the terminal along side matlab without issue.  Likewise, thunderbird runs fine with the previous programs (plus a whole whack more) running simultaneously.

Any  suggestions?

Bryan

PS: thunderbird crashes even if matlab is just idle.
PPS: I am not running matlab in network/server mode

---

### Post by XCan on 2009-07-27
Does the same thing happen if you run matlab with -nodesktop or -nojvm flags?

---

### Post by dainus on 2009-07-28
I am experiencing similar problems. I'm using Ubuntu 9.04, MATLAB 7.8.0 (R2009a), and Thunderbird 2.0.0.22. Both MATLAB and Thunderbird start OK by themselves, but if I try to start Thunderbird whilst MATLAB is already running it fails - it produces an application screen (without any messages shown) then quits after less than a second.

Some minor differences from Warthaug's symptoms: starting MATLAB when Thunderbird is running does not crash the latter, and if I quit MATLAB then Thunderbird starts OK.

I'm not running MATLAB in network/server mode. I am running it in GUI mode.

I tried XCan's suggestions of running MATLAB in -nodesktop or -nojvm mode and they allow Thunderbird to run fine - however this is not suitable for my needs.

Any suggestions?

---

### Post by XCan on 2009-07-28
I would first check with JRE you are using. OpenJDK is known to cause issues. Also, just for the sake of it, try disabling desktop effects. I am Matlab R2009a with sun's java and thunderbird.

---

### Post by Warthaug on 2009-07-30
Thanx everyone for your replies.  I tried everything recommended here and nothing has helped.  Stubbornness seems to be the solution - keep opening thunderbird, and eventually it'll run - at least for a while.

I upgraded to 2009a, and things are a little better, but the occasional crash still occurs.

Bryan

---

### Post by jofre on 2009-10-13
amazing! I am having a very similar problem.

But I have notice that is actually the "lightning" add-on I use in Thunderbird, because if I have Matlab open, I can go to command line and type:
 thunderbird -safe-mode

(which disables any add-on module)

and I have no trouble, well except that I can't see my agenda...

Jofre

---

### Post by Warthaug on 2009-10-13
> **jofre said:**
> amazing! I am having a very similar problem.

But I have notice that is actually the "lightning" add-on I use in Thunderbird, because if I have Matlab open, I can go to command line and type:
 thunderbird -safe-mode

(which disables any add-on module)

and I have no trouble, well except that I can't see my agenda...

Jofre

That's the same problem on my end.  Simple fix, but damn; not being able to see the calendar is a PITA!!!

Bryan

---

### Post by vlg on 2009-11-18
I confirm the aforementioned problem in 9.10 also. The only solution is to disable lightening. :mad:

---

### Post by oldario on 2009-11-26
I experienced the same problem with matlab 2008b and thunderbird 2.x
I solved the problem by changing the default jvm used by matlab by adding a line like
EXPORT MATLAB_JAVA=/the/path/of/your/jvm
in the matlab script that launch matlab.
The jvm that i'm using is from the sun-java6 (/path/to/jvm/java-6-sun-1.6.0.16/jre/ more precisely)
Since this change, no more crashes with thunderbird !

edit: i'm under ubuntu 9.10

---

