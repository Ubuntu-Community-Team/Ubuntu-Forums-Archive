---
title: "How do you make PS1 changes permanent?"
date: 2010-05-19
forum: General Help
---

### Post by Alexander D. Gray on 2010-05-19
Hello everyone,

I'm running Ubuntu 10.04 and I've been looking to customize what's given as my command prompt, and I learned how to do this by entering PS1="*desired text*" which is remarkably straight forward.

I'm a little stuck on how to make this permanent though. If you just type in that command, then when you close that terminal session and open a new one, it resets to the old/default prompt. I read the tutorial at:

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

and it referred to editing the .bashrc file in ubuntu. I found the bash.bashrc file in /etc/ and edited the line that said PS1=, however it didn't change my command prompt. I searched for other files relating to bash and in clear instances that PS1= was given, I changed it to see if the command prompt would change. This has been to no avail so far though.

Does anyone know which file needs to be edited/what needs to be done in order to make a customization of the command prompt permanent?

Thanks in advance.

---

### Post by angry_johnnie on 2010-05-19
the file would be .bashrc.

you're not that far off.

mine, for example is

```
if [ "$color_prompt" = yes ]; then
    PS1=':-) '
else
    PS1=':-) '
fi
```

so my prompt is a smiley face

---

### Post by Alexander D. Gray on 2010-05-20
> **angry_johnnie said:**
> the file would be .bashrc.

you're not that far off.

mine, for example is

```
if [ "$color_prompt" = yes ]; then
    PS1=':-) '
else
    PS1=':-) '
fi
```so my prompt is a smiley face


Thanks for the quick reply, I suppose I'm stuck asking the newbie question of.... where is this .bashrc file? I did a search for bashrc and my results were bash.bashrc located in two places, and then dot.bashrc also located in two places.

Would you mind telling me where it is or how to find it?

Cheers.

---

### Post by capscrew on 2010-05-20
> **Alexander D. Gray said:**
> Thanks for the quick reply, I suppose I'm stuck asking the newbie question of.... where is this .bashrc file? I did a search for bashrc and my results were bash.bashrc located in two places, and then dot.bashrc also located in two places.

Would you mind telling me where it is or how to find it?

Cheers.

The *.bashrc* file you want to use is in your home directory.  This customizes the bash shell that you open, but not other users.  The leading dot(.) makes it a hidden file.  To see this in your your home directory, open the terminal and try this```
ls -al | grep .bash
```

---

### Post by akakingess on 2010-05-20
You could also open your home directory and hit CTRL + H (I think that's the keyboard shortcut) and then you will see all of the hidden files.

---

### Post by Alexander D. Gray on 2010-05-20
> **akakingess said:**
> You could also open your home directory and hit CTRL + H (I think that's the keyboard shortcut) and then you will see all of the hidden files.


CTRL + H is the correct shortcut and I found the proper file to customize my prompt. Thanks for all the help, I would have never guessed that a ' . ' refers to a hidden file, I figured it was an extension of some sort... Learning quickly =D

Cheers.

---

### Post by akakingess on 2010-05-20
Anytime, and that's what keeps me coming back to this forum, plenty of knowledgeable people willing to help (I am not one of the knowledgeable ones, just happened to know that keyboard shortcut), and everyone is friendly to so-called noobs as we all know that we were there once as well. Welcome and stay in touch.

---

