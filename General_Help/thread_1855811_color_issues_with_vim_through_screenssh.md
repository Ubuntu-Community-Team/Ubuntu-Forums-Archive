---
title: "color issues with vim through screen/ssh"
date: 2011-10-07
forum: General Help
---

### Post by ShapeShifta on 2011-10-07
I have been teaching myself how to remote into my desktop from my laptop and have gotten as far as getting 256 colors working within the terminal and screen. I am using the molokai theme and they show up correctly in gvim and vim running in the terminal/screen locally on the desktop or laptop. When running all that through ssh remotely(to desktop) the molokai colors are not the same.

I followed [http://www.frexx.de/xterm-256-notes/](http://www.frexx.de/xterm-256-notes/) and [http://vim.wikia.com/wiki/256_colors_in_vim](http://vim.wikia.com/wiki/256_colors_in_vim) , as of now I'm stuck with an annoying issue, but I can probably live with it if it can not be fixed. I'll get a screenshot uploaded of vim running remotely and locally, soon.

---

### Post by ShapeShifta on 2011-10-07
Ok here is a screenshot of what I explained. On the left is vim running locally in the terminal/screen. On the right is vim running remotely in screen and ssh.

---

### Post by KeyserSoze93 on 2011-10-07
Try forcing vim to use 256 by running

:set t_Co=256

Do other applications support 256 colours over SSH (there's several  scripts around which will make the terminal show you all the colours it can handle.)

I had lots of issues with this, but it was partly because I was also using a custom built of rxvt-unicode. I've not got that experience with Xterm itself for fancy stuff like colours.

---

### Post by ShapeShifta on 2011-10-07
Yea I have tried all that, it's even happening in putty so it may be something else entirely. irssi shows up fine, they match locally and remotely. I did run some of the color scripts found at one of the links i posted and everything came out 100% fine.

---

### Post by ShapeShifta on 2011-10-17
I never really found out what the issue was, but I upgraded both PCs to 11.10 and copied all the configs related to screenrc, vimrc and bashrc, surprisingly everything seems to show up correctly now. I guess I'll consider it resolved.

---

