---
title: "Command line SIP?"
date: 2012-03-04
forum: General Help
---

### Post by jafingi on 2012-03-04
Hi guys,

I hope this is posted in the right category. Found it difficult to find one to the subject. 

What I'm looking for is a command line tool that can make SIP/VoIP calls. 

I would like to make a script that did the following:

1) Call a number
2) Play a .wav (or whatever file)
3) Record what the receiver says to a file
4) Hang up

So.. Just like a "reverse" call answering machine.   

Is this even possible with current software? If so, what would you recommend?

I find the script "pretty" straightforward:

1) Make the call using SIP program to the number
2) When receiving "answered" signal from the SIP, play back .wav to the "input" that SIP program listens to. 
3) I know that the .wav file length is e.g. 16 seconds, so after 16 seconds, it should automatically record the output from the SIP program (where the receiver talks)
4) Wait 30 seconds, and then hang up. 

Thanks in advance!

---

### Post by Zill on 2012-03-04
jafingi:  [Linphone]("http://www.linphone.org/eng/documentation/guide/linphonecsh-control.html") (in the repos) has a CLI that should initate SIP calls as you requested.

However, I will leave others to suggest the best way of playing back and recording audio during the subsequent call.

---

