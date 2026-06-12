---
title: "Ubuntu for Illiterate (like, what's a computer? illiterate)"
date: 2011-08-12
forum: General Help
---

### Post by cblah001 on 2011-08-12
I recently taught my mother how to use a computer (one of the biggest mistakes of my life), check email, and talk to friends on Facebook. She is using my OLD laptop which is running Windows Vista and runs like a dog.

If I were to install a version of Ubuntu and set it up for wireless etc., do you think she will be alright without me so long as she is only using it for the WWW? She lives very far away so unless I can use remote desktop, there is not much support for her.

I have also been throwing around the idea of trying to set her up a flash drive with Google Chrome Flow on it but I am not sure how well that computer will accept it. Also, it is still pretty early in the OS so a lot of hardware is not supported.

Thank you.

---

### Post by timgood on 2011-08-12
My mum is nearly 80 and is a happy Ubuntu user. She loves it. My 'technical callout' requirement has dropped dramatically since I installed it for her. I love it.:D

---

### Post by CatKiller on 2011-08-12
Any version will likely be fine. Xubuntu or Lubuntu might run better if the hardware isn't very powerful. The hardest part generally is unlearning Windows, which isn't a problem in this case.

My mother (74 years old and a complete technophobe) managed perfectly fine with Xubuntu. After a hard drive failure she even re-installed it herself (with a bit of prompting). She'd been terrified of using Windows previously, but got on really well with Linux.

If hardware specifications aren't a problem, I'd recommend that she use the same thing as you do. It makes troubleshooting over the phone easier if the things she can see are called the same as the things you can see.

---

### Post by cblah001 on 2011-08-12
Thanks for the replies. I think I will go ahead and set her up next time I see her. I feel bad but I sometimes don't answer her calls because 50% of the time it is a Vista-related issue that makes me want to hang myself. I may as well have burned my cash instead of buying her "Windows for Dummies".

I hope this works or it looks like a Chromebook is in her future. You can't really mess up going to the web when your OS is the web.

Thanks again

---

### Post by aeiah on 2011-08-12
a web browser is a web browser. she shouldnt have much of a problem, you'll find it easier to fix, and it should run quicker.

if she really only needs a browser and nothing else, you could lock things down so all that's available is the browser

---

### Post by flipper T on 2011-08-12
i am timgood's mum & he is a very naughty boy.

visit me more !

ps can you install arch linux for me, i hear its easy

pps clean your room

---

### Post by Henkdroid on 2011-08-12
Try Jolicloud it is easy to use, think iPad on yor computer, you can also try it in your browser, and it's free.

---

### Post by rountrey on 2011-08-12
I would suggest using KDE or LXDE. I did the same thing with my mom when she complained that her XP laptop was slow. I put Ubuntu 9.04 on it (not KDE), it took a lot of phone calls and visits but she finally got comfortable with it. In hindsight I should have either used KDE, LXDE, or made Gnome look more like XP, it would have save me a lot of time.

Other ideas I have come up with in my experience:
-remove the eye candy that KDE uses and any unnecessary programs, if she is like my mom then it will cause you to answer a lot of questions
-make a separate account for her that is not in the sudoers 
-remove all links to the terminal
-set up remote desktop so you can show her stuff easily with out trying to explain it over the phone or going over there
-have ssh access from the outside, you may need to configure her router for port forwarding on ssh, vnc, and ssh -X.

So, that's it, I made a new Linux convert and pissed off my sister because she had almost convinced my mom to get a Mac. Even though I did spend frustrating hours trying to teach my mom a new OS it was still a win for me.

BTW, my mom's laptop is over 7 years old, been running strong on Ubuntu for the last 2. The only thing I have done to it is replace the hard drive (for space, not for failure).

---

### Post by cblah001 on 2011-08-12
You would be surprised how difficult it is to get her to internet explorer (I have firefox open for her upon startup) since her email will not work with firefox. She learned to type on a Selectric if that puts things in perspective.

I will give some of your suggestions a try and figure out which will be the least daunting for her to figure out.

Gotta love the Ubuntu community for the help.

---

### Post by CatKiller on 2011-08-12
You'd find it quite difficult to get me to use Internet Explorer too.

Your mother's not stupid, just inexperienced. If there's something that she wants to do, then she'll manage. If she doesn't want to do it, she'll find no end of reasons not to. Especially if it means she gets a conversation with her son...

For the most part, the OS won't matter at all. Your mum's unlikely to want a bitching Conky setup, or dual monitors, or anything like that. She's unlikely to play around with anything important. Give her a separate /home partition so that it's easy to keep her stuff if anything goes wrong and you'll probably only have to do the LTS -> LTS transition every couple of years.

Good luck!

---

### Post by Maheriano on 2011-08-12
[IMG]http://imgs.xkcd.com/comics/mac_pc.png[/IMG]

---

### Post by dnguyen1963 on 2011-08-12
I am surprise that Fubuntu or PCLinuxOS have not been mentioned.  They are great for older computer and novice.  Ubuntu 10.04 LTS can be problematic on some older computers, especially with random freezes.  Xbuntu might be fine as mentioned in previous posts.

---

### Post by cblah001 on 2011-08-19
Thank you everyone for the replies.

I did a bit of research and a little testing out to figure out which would be best for her. I put Joli OS on a USB and loaded it on my computer. It looks good for what she needs but if her wireless goes out we will have a problem.

I like the idea of PCLinuxOS since it is similar to what she is kind of used to. She really just needs something less problematic than Windows Vista and I think she will be fine. Once I get her set up with something I will take the suggestion of getting rid of any extra things that may confuse her.

Thanks again!

---

