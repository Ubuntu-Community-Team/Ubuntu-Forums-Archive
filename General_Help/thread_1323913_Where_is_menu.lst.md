---
title: "Where is menu.lst?"
date: 2009-11-12
forum: General Help
---

### Post by sudulo on 2009-11-12
[COLOR="Blue"][SIZE="4"]Hello, everyone. 

I installed Ubuntu 9.10 a few days ago. One of the first things I do when I get a new installation is to change the default operating system into Windows, since I share computers at work, and most people, unfortunately, do not know what Linux is, or how to use it.
 
But this time I have been unable to locate the file menu.lst. In fact I discovered it only in the docs directory. I suspect this version of Ubuntu has a different way to edit the starting menu. 
Any ideas how to achieve this?

Thanks, 
[RIGHT]Sudulo[/RIGHT][/SIZE][/COLOR]

---

### Post by anubhavrocks on 2009-11-12
See this:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by mafa on 2009-11-12
this should help
```
sudo startupmanager
```

---

### Post by sudulo on 2009-11-12
Thanks a lot, anubhavrocks.

---

### Post by sudulo on 2009-11-12
Thanks, mafa. That was concise, yet I hope useful.

---

### Post by Zoot7 on 2009-11-12
Another link on Grub 2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by sudulo on 2009-11-12
> **Zoot7 said:**
> Another link on Grub 2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[SIZE="4"][COLOR="Blue"]
I really thank you guys. There is a lot of information you are giving me, but you may not be aware of a side effect of all these documents you are referring me to: I am no computing guru and I an not going to earn my living with computers, not at least with operating systems or software, not to talk about hardware... So, this kind of answers, which I really appreciate as something very positive, cannot avoid letting me think, that many other people who, like myself, use computers just as a tool to do something which could be done with much more difficulty without it, **when they come to these lecturing documents, are scared away**. Sure, guys, knowledge is ok. But too much, the same as good wine, can be too much for some people who are not used to it. 

On the other hand, I found a simple recipe from another thread I came across a few minutes ago (yes, you are right, I should have read that before I started making questions, but then: do you know how many threads and messages are there to read before I come to the one I need?). So for the benefit of the unlearned --such as myself am--, I will show the two lines which solved my problem:

[LIST=1]
[*]Edit /etc/default/grub with any editor as a root.
[*]Execute "update-grub" without the inverted commas, of course
[/LIST]
And then my "still more ignorant than me" colleagues will stop grumbling at me and my *funny things* in everybody's computer.

Please, don't shout too much at me. :-)

So long, guys,
[RIGHT]Sudulo[/RIGHT]
[/COLOR][/SIZE]

---

### Post by steveneddy on 2009-11-12
The "**inverted commas**" are called quotation marks (rarely referred to inverted commas), 

and please make your font smaller.

Lecturing documents?

[Here is a link]("http://ubuntuguide.org/wiki/Ubuntu:Karmic") from my sig that you might find......entertaining.

---

### Post by sudulo on 2009-11-13
Though it is a very interesting link, it is a small favour you are doing to Ubuntu, if you demand from new users to study such long documents just to start using it. Nothing more reprehensible than the agressive atitude of RTFMers. If you can help, blessed you may be, if you cannot or have not such an intention, sit back and see if anyone does.

---

### Post by Zoot7 on 2009-11-13
> **sudulo said:**
> [SIZE="4"][COLOR="Blue"]
I really thank you guys. There is a lot of information you are giving me, but you may not be aware of a side effect of all these documents you are referring me to: I am no computing guru and I an not going to earn my living with computers, not at least with operating systems or software, not to talk about hardware... So, this kind of answers, which I really appreciate as something very positive, cannot avoid letting me think, that many other people who, like myself, use computers just as a tool to do something which could be done with much more difficulty without it, **when they come to these lecturing documents, are scared away**. Sure, guys, knowledge is ok. But too much, the same as good wine, can be too much for some people who are not used to it. 
[RIGHT]Sudulo[/RIGHT]
[/COLOR][/SIZE]
Fair enough, to answer your query directly, the easiest way to do it would be to use the startup manager.
System -> Administration -> Startup-Manager
And select Windows from the default operating system drop down menu.

---

### Post by steveneddy on 2009-11-14
> **sudulo said:**
> Though it is a very interesting link, it is a small favour you are doing to Ubuntu, if you demand from new users to study such long documents just to start using it. Nothing more reprehensible than the agressive atitude of RTFMers. If you can help, blessed you may be, if you cannot or have not such an intention, sit back and see if anyone does.

I'm glad that you seem to have solved your issue, but I am not aware of the "simple version for beginners" Ubuntu or Linux help pages.

The links in my sig are the way that the information, for the most part, is presented. I suppose that you need to become accustomed to this type of informational format.

There are books and Google for a new user to learn about Linux and Ubuntu. Linux is not Windows and you will find that information is presented in this manner more often than not. The learning curve is very steep for some and this very fact is what scares some beginner types from using Ubuntu or Linux of any type.

Just knuckle down and read each line and try and comprehend what you are reading. If you have an issue or just don't understand what you are reading, post your question in the forums.

Good luck.

EDIT:

Let me make clear that I am not trying to deter you from using Ubuntu. 

I encourage you to take the bull by the horns, dive in to the deep end of the pool, and start learning about your new operating system.

But I must add, if Ubuntu or some other variant of Linux just isn't cutting it for you or any other individual, then use the operating system that you feel most comfortable with. Whether that is Ubuntu, Windows or Mac, the bottom line is that it is all about choice and you are the one that chooses what you want to use.

Will it be easy at first? Probably not. Would it be any easier with a Mac? Probably not. Just one thing, don't give up.

---

### Post by sudulo on 2009-11-16
Thanks a lot Zoot7. Your message was most useful.

---

### Post by sudulo on 2009-11-16
> **steveneddy said:**
> I'm glad that you seem to have solved your issue, but I am not aware of the "simple version for beginners" Ubuntu or Linux help pages.



You seem not to have understood my message. 
If Ubuntu is only for the learned, poor Ubuntu!
If Ubuntu is meant to help everyone, people who want to help must be ready to help everyone not only the gurus, who do not need any help, anyway.

---

