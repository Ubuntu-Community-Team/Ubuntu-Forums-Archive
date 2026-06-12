---
title: "Help with a Terminal command."
date: 2010-11-17
forum: General Help
---

### Post by David802 on 2010-11-17
Hey guys! So I hope I got this in the right section... Idk if this would be considered a beginners question or just general.

I used the command
> sudo rfkill unblock wifi

to fix my wifi about two weeks ago. Now I'm playing with BackTrack 4 Final and have the same issue as I did with ubuntu... But the command doesn't work in BT4. 

Any ideas for what I could use instead?

Thanks so much for the help guys xD

---

### Post by dcstar on 2010-11-17
> **David802 said:**
> Hey guys! So I hope I got this in the right section... Idk if this would be considered a beginners question or just general.

I used the command


to fix my wifi about two weeks ago. Now I'm playing with BackTrack 4 Final and have the same issue as I did with ubuntu... But the command doesn't work in BT4. 

Any ideas for what I could use instead?

Thanks so much for the help guys xD

You are asking a question about a non-Ubuntu system in a Ubuntu forum specifically for:

***All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu.***

Do you really expect a useful answer?

---

### Post by David802 on 2010-11-17
> **dcstar said:**
> You are asking a question about a non-Ubuntu system in a Ubuntu forum specifically for:

***All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu.***

Do you really expect a useful answer?

Theres no reason to be a jerk dcstart....Pardon my assumption that there are people in this world that have used both Ubuntu and BT4... 

Anyway, I'll rephrase the question... Can anybody explain to me what the command "rfkill unblock wifi" does in Ubuntu? What's it unblocking... Does rfkill mean that its resetting the radio on my wifi card?

---

### Post by asmoore82 on 2010-11-17
It's worth noting that Backtrack4 is Ubuntu-based.

---

### Post by David802 on 2010-11-17
Ubuntu 8.10 if I remember the backtrack website faq correctly.... Thanks for reminding me asmoore82

further more... (this is so it can be seen that im not JUST relying on the forum for answers here.) 

When I type 

> man rfkill

into my terminal I get this....

> No manual entry for rfkill
See 'man 7 undocumented' for help when manual pages are not available.

When I tried to run "mandb" as the document it suggested says it doesn't do anything.

---

### Post by dcstar on 2010-11-17
> **David802 said:**
> Theres no reason to be a jerk dcstart....Pardon my assumption that there are people in this world that have used both Ubuntu and BT4... 
.......

So those that have used BT4 will clearly jump to your aid because that can see from the Title that this is related?

Don't you think that your specific BT4 issue would be better addressed here:
[http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)
Chances are you would probably have an answer by now had you posted there in the first place.

---

### Post by dcstar on 2010-11-17
> **David802 said:**
> Ubuntu 8.10 if I remember the backtrack website faq correctly.... Thanks for reminding me asmoore82
.......

[http://linuxwireless.org/en/users/Documentation/rfkill](http://linuxwireless.org/en/users/Documentation/rfkill)

---

### Post by nickleboyblue on 2010-11-17
The command you used isn't meant to "unblock" anything per-se.  It's meant to enable/disable the interface.  Essentially what you did was enabled all wifi devices on your computer instead of focusing on a single interface, because you specified "wifi" instead of an index.  To find out which interfaces on your computer are controlled by rfkill, run:

```
rfkill list
```

That gives you a list of all interfaces on your computer and their corresponding index numbers.  Use the index to specifically enable/disable an interface.

As for the connectivity issue, most likely it has nothing to do with software and everything to do with the wireless network you are using.  That still leaves this as a non-ubuntu issue, and you should probably take this up with your network administrator.

---

### Post by David802 on 2010-11-17
> **dcstar said:**
> So those that have used BT4 will clearly jump to your aid because that can see from the Title that this is related?

Don't you think that your specific BT4 issue would be better addressed here:
[http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)
Chances are you would probably have an answer by now had you posted there in the first place.

dcstart I did ask this question on the BT4 forums but hadn't gotten a response when I left for work for the night. 

If you'd lower your nose for a few minutes and take a look at your monitor screen you'll probably be able to find my post on there forums as well. I believe I used the same screen name when creating an account. Unfortunately for me I've got 10 hours before I can go to a computer that will let me go to the backtrack forums.

I'll thank you to kindly add me to your ignore list, that way you don't have to read my poorly written title, and I don't have to read your arrogant dribble. I'd add you but I don't see that I Should have to since its YOU that is taking such offense at how I wrote my Title. Would you rather have had me type "PLEASE HELP!!!!!"? 

The purpose of this topic was to get help with a terminal command, hence the title. Anybody with some Ubuntu experience may be able to shed some light on a terminal command. I chose to target that audience rather than the much smaller audience that may be experienced in both Ubuntu and BT4.

---

### Post by David802 on 2010-11-17
> **nickleboyblue said:**
> The command you used isn't meant to "unblock" anything per-se.  It's meant to enable/disable the interface.  Essentially what you did was enabled all wifi devices on your computer instead of focusing on a single interface, because you specified "wifi" instead of an index.  To find out which interfaces on your computer are controlled by rfkill, run:

```
rfkill list
```

That gives you a list of all interfaces on your computer and their corresponding index numbers.  Use the index to specifically enable/disable an interface.

As for the connectivity issue, most likely it has nothing to do with software and everything to do with the wireless network you are using.  That still leaves this as a non-ubuntu issue, and you should probably take this up with your network administrator.

Thank you very much for the explanation.

---

