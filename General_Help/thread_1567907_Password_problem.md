---
title: "Password problem"
date: 2010-09-04
forum: General Help
---

### Post by jimmynCR on 2010-09-04
I opened the Terminal and typed sudo apt-get install zanity and it ask for password. I typed my Ubuntu password, but nothing happened. I there a place to open a Terminal password.

---

### Post by Pollox on 2010-09-04
Terminal will not give you any feedback (no stars will appear) when you type your password for sudo.  Just type it and press enter when you're done.

---

### Post by sikander3786 on 2010-09-04
And this is intended for security so that nobody sitting besides / standing behind could even guess the password by counting the characters. Some close friends who know your likes and interests can do that. It is most of the times someone's name, or cell no. etc.

Regards.

---

### Post by Joe of loath on 2010-09-04
Yup, if you know the number of characters a bruteforce is a large amount faster than trying out all the combinations up to 15 characters or whatever.

---

### Post by aysiu on 2010-09-04
> **sikander3786 said:**
> And this is intended for security so that nobody sitting besides / standing behind could even guess the password by counting the characters. If that's the intent, then it fails. Anyone sitting besides or next to you can count the clicks on your keyboard and/or just look at the keys you're pressing. She can definitely count the clicks just to get the number. She may not remember all the keys she saw you pressing, but seeing some or most of them is definitely better for compromising security than looking at a bunch of asterisks.

More details here:
[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)

---

### Post by sikander3786 on 2010-09-04
> **aysiu said:**
> If that's the intent, then it fails. Anyone sitting besides or next to you can count the clicks on your keyboard and/or just look at the keys you're pressing. She can definitely count the clicks just to get the number. She may not remember all the keys she saw you pressing, but seeing some or most of them is definitely better for compromising security than looking at a bunch of asterisks.

More details here:
[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)

If thats not the reason, then what is the reason behind it? Clicks or keystrokes are not that easy to count. Why the developers rejected to correct that inconsistency?

And it might be a she or he sitting besides... Why did you focus on she? ;)

---

### Post by aysiu on 2010-09-04
> **sikander3786 said:**
> If thats not the reason, then what is the reason behind it? People who have used *nix terminals for decades are used to it. For more details, read [Entering password in Terminal gives no visual feedback](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

> Clicks or keystrokes are not that easy to count. They're easier to count than asterisks, especially when you get beyond seven or eight asterisks in a row.

> Why the developers rejected to correct that inconsistency? Because they're worried about offending certain key demographics. See comments in the above bug report for more details.

> And it might be a she or he sitting besides... Why did you focus on she? ;) Why do people usually focus on "he"?
[Why I say she](http://www.psychocats.net/ubuntucat/why-i-say-she/)

---

### Post by sikander3786 on 2010-09-05
> **aysiu said:**
> People who have used *nix terminals for decades are used to it. For more details, read [Entering password in Terminal gives no visual feedback](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

 They're easier to count than asterisks, especially when you get beyond seven or eight asterisks in a row.

 Because they're worried about offending certain key demographics. See comments in the above bug report for more details.

 Why do people usually focus on "he"?
[Why I say she](http://www.psychocats.net/ubuntucat/why-i-say-she/)


You won. Agreed. Got it. You've got logic behind whatever you said "he or she".

Still I don't agree what you said about passwords in terminal. There must have been some reason for giving back no visual feedback for passwords in unix itself. Google should enlighten me.

Regards.

---

### Post by aysiu on 2010-09-05
> **sikander3786 said:**
> 
Still I don't agree what you said about passwords in terminal. There must have been some reason for giving back no visual feedback for passwords in unix itself. Google should enlighten me. There was a reason, and it's no longer relevant. From [Idea #11118: Display *** for password in the terminal](http://brainstorm.ubuntu.com/idea/11118): [quote=arand]It is a security feature, albeit more relevant when looking at the history of Unix.

Looking back at the time when your output was printed out on physical paper, it makes a lot of sense to not print out asterisks so that anyone shuffling through the printout would be able to see the length of your password.[/quote]

---

### Post by mendhak on 2010-09-05
The password typer would have to be pretty slow if you want to be able to count the number of key clicks.  Most users, familiar with their own passwords, usually type it pretty fast so you'd either have to 

a - get them to type the password repeatedly
b - ask them to slow down so that you can count the key clicks
c - hope they have a short password

But yeah, knowing a few keys could help if you're attempting to guess or brute force.

---

### Post by aysiu on 2010-09-05
> **mendhak said:**
> The password typer would have to be pretty slow if you want to be able to count the number of key clicks. And, by the same logic, a password would have to be awfully short for you to be able to count the number of asterisks.

---

### Post by lisati on 2010-09-05
<off topic>
> **aysiu said:**
> [Why I say she](http://www.psychocats.net/ubuntucat/why-i-say-she/)
"It" doesn't quite make the grade when referring to people, but otherwise makes a useful gender-neutral word. In a way, the Samoans might be on to something when they use "ia" for "he", "she" and "it". Then again, they have **three** words for "you" - "'oe" for one person, "oulua" for two people and "outou" for more than two. :D
</off topic>

---

