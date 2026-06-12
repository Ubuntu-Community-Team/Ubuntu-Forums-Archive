---
title: "ThinkFinger on Karmic - Can't"
date: 2010-04-01
forum: General Help
---

### Post by SysterNeoX on 2010-04-01
Hi all!

I've recently bought a IBM X41 Tablet. It comes with fingerprint reader, which actually works on thinkfinger drivers (i can see my finger matched when i use tf-tool).
However i have problems to get it working with PAM as a basic security method
I've made all the steps described here: [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Karmic]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Karmic")
Also, i've added a fingerprint group and added myself into it.
But now i got some problems.
First of all, when i try to add my fingerprint:
"sudo tf-tool --acquire $USERNAME" 
Program hangs at point "Storing data...". Verbose mode run don't show me anything. 
And when i restart system i can't log into system. I got "Password or swipe fingerprint", but when i swipe finger, or enter a password i get "Service cannot access..."
What's wrong with it?

---

