---
title: "Java install directory &amp; JAVA_HOME variable?"
date: 2006-03-24
forum: General Help
---

### Post by jms830 on 2006-03-24
I am trying to run MusicMagicMixer, but I have to set my java home variable.  However, I keep looking around and I find all these guides, but none of them say what the default install directory for java is if "apt-get install sun-j2re1.5" is used. Can someone please help me out? And if anyone knows anything about getting MusicMagicMixer to work, let me know.

**EDIT:** for instance, I need to do something like this but I can't find where mine is
"you may also need to set the JAVA_HOME system variable to point to the
directory where you've installed java, i.e.
JAVA_HOME=/usr/local/java/jre-1.5.0, you should be able to set this in
you .bashrc file so that it's exported every time the system starts.
One of the entries in my ~/.bashrc file is:

export JAVA_HOME=/usr/local/java/j2sdk1.4.2_06"

---

### Post by moshstef on 2006-03-24
On my setup java was installed in /usr/lib/j2re1.5-sun 
Check if it is there.

---

### Post by jms830 on 2006-04-03
yes, it was there. thank you.

---

