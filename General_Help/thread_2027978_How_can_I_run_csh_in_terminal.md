---
title: "How can I run csh in terminal?"
date: 2012-07-17
forum: General Help
---

### Post by epikvision on 2012-07-17
I like using the terminal and came to learn that it goes by the Bourne Again Shell (bash).  Then I see that I could use the terminal as a C shell too (csh), but I don't know how to run it. 

I installed csh from the Ubuntu software center. I type csh in the terminal, and all that comes out is the % sign.  Is this the c-shell? How can I set my terminal to run csh when I don't want to run bash?

---

### Post by spjackson on 2012-07-17
The % is the default prompt for csh. You can run csh simply by typing csh at the bash prompt. If you want your default login shell to be csh, then you should be able to change it with the chsh command.

---

### Post by cortman on 2012-07-17
> **epikvision said:**
> I installed csh from the Ubuntu software center. I type csh in the terminal, and all that comes out is the % sign. Is this the c-shell?


Yep, that's it. A bit limited- you'd need to edit your prompt to get it to look like bash.

> **epikvision said:**
>   How can I set my terminal to run csh when I don't want to run bash?


By doing what you just did- or else define "when you don't want to run bash" a little more clearly. :)

While we're talking shells, I'll give a little shout-out for my favorite- zsh.

---

### Post by Lars Noodén on 2012-07-17
> **spjackson said:**
> The % is the default prompt for csh. You can run csh simply by typing csh at the bash prompt. If you want your default login shell to be csh, then you should be able to change it with the chsh command.

In csh that should be the environment variable [font=Courier New]prompt[/font]

However, csh is not so widely used and there are a lot of [reasons to avoid it](http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/).

zsh was already mentioned.  ksh is another good one, it is in wide use in a lot of non-GNU distros.

---

### Post by lukeiamyourfather on 2012-07-17
> **Lars Noodén said:**
> 
However, csh is not so widely used and there are a lot of [reasons to avoid it](http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/).


I'll second that. To the original poster, are you trying different shells just because you can or are you interested in csh for a specific reason/purpose?

---

### Post by dcottingham on 2012-07-17
Two things I'd add to the above:

1. Both bash and csh distinguish "login shells" from plain shells -- without getting into too many boring details, if you want to see the "login shell" version of csh say "csh -l". This is also the behavior you'll get if you use chsh to make this your default shell, as was mentioned above. (I only mention this because you seemed disappointed by the "%" prompt.)

2. There is some anti-csh sentiment out there, which should be taken with a grain of salt -- but I'm left wondering why you're interested in switching. Unless you're writing scripts, the differences between these shells are pretty small.

---

### Post by epikvision on 2012-07-18
> **dcottingham said:**
> ... but I'm left wondering why you're interested in switching. Unless you're writing scripts, the differences between these shells are pretty small.

Ah well, I'm not exactly interested in switching to csh.  I was just curious if it was alright to see the "%" character looming.

This question resulted as I was reading over a Linux introductory book.  Perhaps, it's a valuable asset to learn the C language?  Is the Linux kernel still based on the C language?

---

### Post by dcottingham on 2012-07-18
The Linux kernel is indeed written in C, but csh is not, in spite of its name, scripted in C. So you won't learn anything about C programming writing csh scripts.

---

### Post by epikvision on 2012-09-27
Alright, everyone.  Thanks for the valuable replies.

---

