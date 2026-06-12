---
title: "Problem with TTY Fonts - KDFONTOP: Invalid argument"
date: 2011-01-15
forum: General Help
---

### Post by zia.newversion on 2011-01-15
I was trying to change the console fonts. I remember that I did successfully change the console fonts back when I was using Jaunty with this:

```
setfont <fontname>
```

Where ```
fontname
``` was any terminal font listed in ```
/usr/share/consolefonts/
```

Now I have Maverick installed. When I switch to TTY and type
```
setfont Lat15-Terminus20x10
```
I get this error
```
putfont: KDFONTOP: Invalid argument
```

Can anyone please look into it and let me know how to achieve what I am trying to?

---

### Post by zia.newversion on 2011-01-16
A very warm welcome from Ubuntu Community!

Does no one know an answer?

---

### Post by zia.newversion on 2011-01-17
No replies yet. Solved anyway.
It appears I had framebuffer disabled. Enabled it by editing the /etc/default/grub and adding vga=792 in the default command line arguments for grub.
If anyone has the same problem, this might be a solution.

---

### Post by zia.newversion on 2011-05-19
There are lots and lots of guides on getting your questions answered quickly... The key points are:
- Present your problem nicely and legibly.
- Be sure to follow the code of conduct of the forum in question.
- You should have at least some basic knowledge of background of your problem.
- And most importantly, moderators hate reposts, so Google your problem first to see if it already has been answered...

If you follow all these guidelines and get no answers, that means people either don't know the solutions or just don't want to answer it...

Strange enough, I try to follow these guidelines very very carefully, yet ever since I have joined the forum, very few of my problems have got satisfactory answers, even after repeated bumping. It is not possible that no one knows solution to any of my problems... Or maybe people don't want to answer my questions... 

No offense, but there might be some reasons for that. But they are all social, ethnic, semi-political and racial. So I shouldn't name them here. But I do mean to ask the moderators, humbly, without any ill meaning, should I change or choose not to display the "Location" in my User CP, (if that would help).

---

### Post by Irihapeti on 2011-05-19
You could try not displaying your location and see if that makes any difference, but I rather doubt that this is the issue. If you hadn't said anything, I for one wouldn't have noticed.

I think it's much more likely that no one knows the answer, or doesn't feel that they know enough to answer adequately. I know that I will often not answer posts because of the latter reason.

My own experience is that it's been a while since I've had an answer to a question that I've posted; I assume that is because I've solved all the basic stuff and the problems remaining are more obscure.

---

### Post by zia.newversion on 2011-05-19
Ha! Thanks...
I think that means I have solved all the basic stuff, right? That means I am progressing. :p

---

### Post by Irihapeti on 2011-05-19
Definitely see it as progress beyond the basics. Maybe not getting responses could be a badge of honour :) (Except of course for those who use an obnoxious style.)

I just had a look at your other posts, and I would say that most of them are about less common things. Unity isn't, but I think that everyone is on a steep learning curve there.

I know that I have a really obscure problem when I post a question, get no answer, then google for an answer and the first hit is my original post! It's happened to me on several occasions, and it's very frustrating.

BTW I used to worry that being a woman might bias people against me, but I think that on these forums, it's made no difference at all.

---

### Post by zia.newversion on 2011-05-19
Thanks for the reassurance, but I still think, given the current circumstances, I should not display my location.

And thanks again. It is comforting to know something that bothers you does bother a few other people as well. :)

---

### Post by Irihapeti on 2011-05-19
You're welcome. I wish you all the best.

---

