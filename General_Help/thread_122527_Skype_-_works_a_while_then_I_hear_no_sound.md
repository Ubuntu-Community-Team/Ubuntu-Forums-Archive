---
title: "Skype - works a while then I hear no sound"
date: 2006-01-27
forum: General Help
---

### Post by it.henrik on 2006-01-27
Ok ... it seems like im the only one in the linux world who have this problem.  I read more forum-threads then I though was possible in the hunt for someone else with this problem, and the solution.

It works like this:
I can connect and talk for a while and then the sound in the output (speakers) dies on me. I cant hear anything. BUT the other person im talking to can hear me perfectly. NOTICE!!! It works for a while, sometimes for 3 minutes, sometimes for 30.

When this happens I can just disconnect and reconnect and it works again.. for a while. I can do this a couple of times and after a few times I get the famous "problem with sound device"-error. I have tried to change over to ALSA according to the most popular howto:s here in the forum. It didnt help either. 

Im all out of ideas here. Someone got any ideas on what it can be or any pointers in the right direction? Best of all... anyone got the solution to my problem?

---

### Post by TechSonic on 2006-01-27
What sound card are you using?  If it's an Audigy then there are some topics already explaing how to fix the duplex sound issue.  If you are using an SB Live 24bit, then there isn't any help at the moment.

If it is SB Live! 24bit, [http://www.ubuntuforums.org/showthread.php?t=122563](http://www.ubuntuforums.org/showthread.php?t=122563)

---

### Post by it.henrik on 2006-01-28
My soundcard is the on-board intel 823801CA/CAM AC'97 Audio Controller. 
My laptop is a DELL C840.
Im running breezy 5.10.
My installed skype is 1.2.0.18_API

I doesnt matter wich skype I install, I get the same behaviour if I install any of the deb:s out there or the tarballs from skype.com with or without Qt.

---

### Post by it.henrik on 2006-01-29
I know we all are really tired of skype post but please gimme som help here :)

Is this a duplex problem? 
How can it be since it works for sometimes 30 minutes before it breaks down?

---

### Post by it.henrik on 2006-02-03
Problem solved. 

I noticed that the sound died when the other side made a louder-then-average sound.

Solution:  turn down mic input level on the other skype clients computer.

---

