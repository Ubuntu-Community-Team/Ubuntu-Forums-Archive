---
title: "purging e16 seems to remove unity launcher"
date: 2011-10-18
forum: General Help
---

### Post by kkruecke on 2011-10-18
I am running Natty with auto-login enable. I installed e16:
#sudo aptitude install e16. 

Then I later did:
# sudo purge e16

Upon rebooting I don't have the unity laucher. I don't know why. Also when I try to do:
$ sudo shutdown now
It never shutsdown. 

So how do I 1.) re-enable the login screen, and 2.) Unity working again?

I tried installing unity-2d, but that didn't do any good. _Any_ help is much appreciated.

---

### Post by kkruecke on 2011-10-18
I tried
# sudo unity --reset
and got this

> kurt@kurt-natty:~$ sudo unity --reset
[sudo] password for kurt: 
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'
kurt@kurt-natty:~$ 


I've got no clue what is happening.

---

### Post by kkruecke on 2011-10-18
Thanks to the article [Missing top and side panels in Unity: Troubleshooting, Ubuntu Natty / Oneiric ]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") I found a solution, using the compiz configuration settings manager.

---

