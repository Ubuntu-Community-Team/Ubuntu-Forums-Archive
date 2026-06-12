---
title: "Problem with the way my command line displays input"
date: 2011-10-29
forum: General Help
---

### Post by ClientAlive on 2011-10-29
Hi,

I'm running Ubuntu 10.04 LTS. several weeks ago I edited .bashrc to change the color of my command line. Everything seemed to be working fine. The web page I went off to know the format is: [http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/](http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/)

Recently I had to type in a rather long command that should have continued onto the next line below. What happened though was that the line just started overwriting the command line itself. Instead of moving to the line below it came back on the far left of the screen on the same line. Just to check test it I just stared typing all kind of letters to see what it would do if I took op a long long space of text. Actually it just keeps overwriting. I overwrites the entire command line on the same line then starts into overwriting the beginning of what I had begun to type.

The output of "echo $PS1" is:

```

\e[0;31m[\u@\h \W]\$ \e[m

```

but the line in .bashrc is:

```

export PS1="\\e[0;31m[\\u@\\h \\W]\\$ \\e[m "

```

See how there's two backslashes not just one?

Anyhow, I put that second one there after seeing that they are doubled in what that web page gives as the default case.

Default case (output from "echo $PS1") according to that web page:

```

echo $PS1

[\\u@\h \\W]\\$

```

I've attached a copy of my .bashrc file in case it may be helpful to see it.

Does anyone know why I might be having the problem I'm having and how I can correct it?
----------------------

Edit:

Seems there's other problems too. When I use the arrow keys to bring up command history the following line print on the next line just fine but there is some portion of the last command that stays at the end of the command line, beginning of the command that comes up from history (one or two words) and just stays there almost like it's an append to the command line. It's after it that the commands from history change/ come up.

---

### Post by hansdown on 2011-10-29
Hi, ClientAlive.

You need to log out, and back in.

These settings, are temporary. 

Unless, you went further, than this screenshot.

---

### Post by ClientAlive on 2011-10-29
> **hansdown said:**
> Hi, ClientAlive.

You need to log out, and back in.

These settings, are temporary. 

Unless, you went further, than this screenshot.


Thanks bro. I'll have to check it out in a bit here and get back. If it solves it I'll mark this thread as solved tho.

---

### Post by hansdown on 2011-10-29
> **ClientAlive said:**
> Thanks bro. I'll have to check it out in a bit here and get back. If it solves it I'll mark this thread as solved tho.

I'm trying to find a "slightly" better link, for what you are looking for.

This may be helpful.

[http://articles.slicehost.com/2010/4/30/ubuntu-lucid-setup-part-2](http://articles.slicehost.com/2010/4/30/ubuntu-lucid-setup-part-2)

Scroll down to, custom prompt.

This one, is wicked better.

[http://www.ibm.com/developerworks/library/l-tip-prompt/](http://www.ibm.com/developerworks/library/l-tip-prompt/)

Scroll down to, colorization, to get the color codes you want.

---

### Post by ClientAlive on 2011-11-03
> **hansdown said:**
> I'm trying to find a "slightly" better link, for what you are looking for.

This may be helpful.

[http://articles.slicehost.com/2010/4/30/ubuntu-lucid-setup-part-2](http://articles.slicehost.com/2010/4/30/ubuntu-lucid-setup-part-2)

Scroll down to, custom prompt.

This one, is wicked better.

[http://www.ibm.com/developerworks/library/l-tip-prompt/](http://www.ibm.com/developerworks/library/l-tip-prompt/)

Scroll down to, colorization, to get the color codes you want.


Thanks hansdown. Sorry it took me so long to get back. I've been sooo busy with school and everything lately.

As to your first post, I had edited the bashrc file manually, added the new line for how I wanted my command line to look and commented out the old one. So rebooting makes no difference, it is permanent. 

No, wait, I just looked at bashrc again with less and I don't see where I had commented out any previous entry. I did see a couple things that includes "PS1" (at least one of which resembles the entry for your command line) and wonder about it a bit. Neither it nor the other are commented out.

The second entry, about half way down the file looks like this:

```

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;


```

Well, in any case I need to get this sorted out. I have a comp sci class that I'm learning C in and would like to do some or all of the work on my own computer now. If my command gets overwritten when it gets too long that kinda throws a wrench in things.

I'm going to those links you gave me right now to see what I can do with the info. If I get it sorted out I'll let you know.

Thanks man.

---

### Post by ClientAlive on 2011-11-03
I got it brother. I just had some things out of place and some things missing. Thanks for those links.

:popcorn:

---

### Post by hansdown on 2011-11-03
You rock, ClientAlive.

Glad you fixed it.

---

### Post by ClientAlive on 2011-11-04
> **hansdown said:**
> You rock, ClientAlive.

Glad you fixed it.


Thanks man.

:)

---

