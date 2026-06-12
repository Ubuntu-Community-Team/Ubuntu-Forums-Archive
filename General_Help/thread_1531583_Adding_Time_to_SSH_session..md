---
title: "Adding Time to SSH session."
date: 2010-07-15
forum: General Help
---

### Post by luccio83 on 2010-07-15
I need some assistance with my Ubuntu server setup.

I use a Free BSD Linux server at work that I SSH to.  When I telnet to the server I see the following:

[8:23am]  myhost:/home/pmiglia]


I like that I see the time and path just like that.


Now I have been trying for DAYS to get my Linux server to display with the time but with no luck

Any ideas on how this was done?

FYI, new users and old users do not display like this when they SSH, only me as far as I can tell.

---

### Post by vikas.sood on 2010-07-15
Modifying Bash PS1 prompt variable should do it.
modify your .bashrc to add following line.

PS1='[\t \u@\h \W]\$'

\t above adds time to the prompt.

save and exit.

source .bashrc

---

### Post by thebigob on 2010-07-15
The above will work.

For a More in depth understanding so you can change this yourself [here]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html") is a very good like for this.

---

### Post by luccio83 on 2010-07-15
> **thebigob said:**
> The above will work.

For a More in depth understanding so you can change this yourself [here]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html") is a very good like for this.


All very useful information however how do I get this to stick!

I found that I believe I need to change the .bash_profile file however the file does not exist, and if I create it it does nothing.

---

### Post by vikas.sood on 2010-07-16
after you finish editing the file with the format of PS1 desired, you need to source that file. That will redefine your session variables. Or else start a new session.

If it does not help paste the contents of your .bashrc

---

