---
title: "I really need help with this!!"
date: 2009-12-03
forum: General Help
---

### Post by ibrahim.k on 2009-12-03
Hi,

I have recently installed 9.10 ubuntu on my laptop
**Hp-dv6 1045**
I have faced this problems

1- when I plug my headphones in the sound keeps coming from the speakers it doesn't stop also it comes out from the headphones 

2- I am using wireless Internet connection but when i plug a network cable the internet connection stops???? the eth1 has manual proxy settings

thnx

---

### Post by quixote on 2009-12-04
(In general, put separate questions in separate threads.  It makes it easier for everyone that way.)

Sound: I had the same issue and it was resolved by updating the ALSA driver to 1.0.21.  I'm not sure what karmic has, but if it's an earlier version, that may be your problem.  Instructions [here]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/").  The problem with that is after a kernel update, you have to do it all over again.  The script [here]("http://ubuntuforums.org/showthread.php?p=6589810") is said to avoid that problem, but I haven't tried it myself yet.

The connection behavior you're describing sounds normal.  Wireless disconnects in favor of wired.  If you pull out the wired connection, the wireless should reconnect again.  Is that not what is happening?  If you don't want it using the wired connection, then is there a problem just not using the cable?

---

### Post by ibrahim.k on 2009-12-05
> **quixote said:**
> 
The connection behavior you're describing sounds normal.  Wireless disconnects in favor of wired.  If you pull out the wired connection, the wireless should reconnect again.  Is that not what is happening?  If you don't want it using the wired connection, then is there a problem just not using the cable?


Dear quixote,
do you mean that I can't use wireless connection in addition to the wired one ?

thank you very much

---

### Post by quixote on 2009-12-05
Yes.  As far as I know, it's not possible to use both at once.  I think it wouldn't make sense from a machine or software perspective.  You're passing through one gateway to the internet, so having two ways of reaching the gateway won't speed anything up.  If you have a special application, or multiple lines of access to the internet, then maybe there are specialized ways of dealing with that.  I'd start a new thread in that case, and make sure the subject makes the multiline nature of the problem clear.

Hope this helps.

---

### Post by ibrahim.k on 2009-12-06
I need this wired connection to connect to local remote server the wired connection doesnt have an INTERNET connection 

Thank you :)

---

