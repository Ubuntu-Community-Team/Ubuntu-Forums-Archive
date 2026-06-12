---
title: "Editing .bash_profile"
date: 2010-10-14
forum: General Help
---

### Post by Tawrtoise on 2010-10-14
I'm trying to learn about the Terminal and shell scripts and functions and such and I'm using [www.linuxcommand.org]("http://www.linuxcommands.org"). But I'm stuck on [this]("http://linuxcommand.org/wss0020.php") page, where he writes an alias at the bottom of .bash_profile.

First of all, I'm a little confused on how to use the text editors. I have vi, gedit, and emacs installed, but I'm not exactly sure how to use any of them.

Any help on this would be appreciated, let me know if there's any details that you need to know that I might've left out.

---

### Post by Sub101 on 2010-10-14
You set alias etc in .bashrc not .bash_profile.

My favorite command line editor is nano.

---

### Post by luvshines on 2010-10-14
Where are you stuck exactly with aliases ?

I personally use only gedit and vim(improved vi) for editing.

1. gedit gives you an advantage of GUI so you can file icons/menus to carry out the tasks. You can find tutorials online

2. For vi, I would suggest installing vim instead. Vim has an excellent built in tutorial. Just open vim, type :help and press ENTER. Vim will be totally command based, and you'll learn as you use. The Gvim is GUI Vim.

---

### Post by Tawrtoise on 2010-10-14
> **luvshines said:**
> Where are you stuck exactly with aliases ?

I personally use only gedit and vim(improved vi) for editing.

1. gedit gives you an advantage of GUI so you can file icons/menus to carry out the tasks. You can find tutorials online

2. For vi, I would suggest installing vim instead. Vim has an excellent built in tutorial. Just open vim, type :help and press ENTER. Vim will be totally command based, and you'll learn as you use. The Gvim is GUI Vim.

Well, where I'm reading it says:

> 
Now, before you become too confused about what I just said, let's make an alias. Make sure you are in your home directory. Using your favorite text editor, open the file .bash_profile and add this line to the end of the file:
   alias l='ls -l'

Now, I get lost at opening .bash_profile. I tried opening it with GVim but it says it's a read-only file. And I'm not sure how to open it with Vim. 
 [FONT=monospace]
[/FONT]

---

### Post by nothingspecial on 2010-10-14
To back up the first to answers.....

Yes, use nano
```

nano .bashrc
```

Add your aliases to the bottom of that file.

When you are done press Ctrl O to save, then Enter

Then press Ctrl X to save

To get bash to read your new aliases type

```
. ~/.bashrc
```

After that, your new aliases will work.

---

### Post by nothingspecial on 2010-10-14
> **Tawrtoise said:**
> Well, where I'm reading it says:



Now, I get lost at opening .bash_profile. I tried opening it with GVim but it says it's a read-only file. And I'm not sure how to open it with Vim. 
 [FONT=monospace]
[/FONT]


Put them in ~/.bashrc 

To show you here is the end of mine

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias pc='ssh -X -C -c blowfish rob@192.168.1.6'
alias suzie='ssh -X -C -c blowfish suzie@192.168.1.3'
alias music='sshfs -o idmap=user rob@192.168.1.11:/home/rob/Music ~/allmusic'
alias slide='sshfs -o idmap=user rob@192.168.1.11:/media/backup/Photos ~/snaps && feh -rzF -D 3 ~/photos'
alias tv='ssh -X -C -c blowfish rob@192.168.1.11'
alias mouse='ssh -X rob@192.168.1.11 x2x -east -to :0'
alias dict='cat /usr/share/dict/words | grep '
#alias read='sshfs -o idmap=user rob@192.168.1.6:/media/backup/comix/ ~/comix'
alias r2='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r1x.asx'
alias r4='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r4.asx'
alias r5='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r5l.asx'
alias r6='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r6.asx < /dev/null &'
alias ran='mplayer -quiet -shuffle -playlist <(find ~/Music -type f) 2> /dev/null'
alias killm='killall mplayer'
alias mtv='sshfs -o idmap=user rob@192.168.1.11:/media/backup ~/tv'
alias cast='ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x600 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless
_ultrafast -threads 0 output.mkv'
alias utube='ffmpeg -i output.mkv -acodec libmp3lame -ab 128k -ac 2 -vcodec libxvid -qscale 8 -me_method full -mbd rd -flags +gmc+qpel+mv4 -trellis 1 -threads 0 vid.avi'
```

That is the end of my .bashrc and those aliases work :)

---

### Post by Tawrtoise on 2010-10-14
> **nothingspecial said:**
> Put them in ~/.bashrc 

To show you here is the end of mine

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias pc='ssh -X -C -c blowfish rob@192.168.1.6'
alias suzie='ssh -X -C -c blowfish suzie@192.168.1.3'
alias music='sshfs -o idmap=user rob@192.168.1.11:/home/rob/Music ~/allmusic'
alias slide='sshfs -o idmap=user rob@192.168.1.11:/media/backup/Photos ~/snaps && feh -rzF -D 3 ~/photos'
alias tv='ssh -X -C -c blowfish rob@192.168.1.11'
alias mouse='ssh -X rob@192.168.1.11 x2x -east -to :0'
alias dict='cat /usr/share/dict/words | grep '
#alias read='sshfs -o idmap=user rob@192.168.1.6:/media/backup/comix/ ~/comix'
alias r2='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r1x.asx'
alias r4='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r4.asx'
alias r5='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r5l.asx'
alias r6='mplayer -really-quiet -playlist http://bbc.co.uk/radio/listen/live/r6.asx < /dev/null &'
alias ran='mplayer -quiet -shuffle -playlist <(find ~/Music -type f) 2> /dev/null'
alias killm='killall mplayer'
alias mtv='sshfs -o idmap=user rob@192.168.1.11:/media/backup ~/tv'
alias cast='ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x600 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless
_ultrafast -threads 0 output.mkv'
alias utube='ffmpeg -i output.mkv -acodec libmp3lame -ab 128k -ac 2 -vcodec libxvid -qscale 8 -me_method full -mbd rd -flags +gmc+qpel+mv4 -trellis 1 -threads 0 vid.avi'
```That is the end of my .bashrc and those aliases work :)

 I don't understand, if they belong in bashrc, why did this tutorial say to put an alias in bash_profile?

---

### Post by nothingspecial on 2010-10-14
> **Tawrtoise said:**
> I don't understand, if they belong in bashrc, why did this tutorial say to put an alias in bash_profile?

Because you can do what you want in linux.

I think (but don`t know for sure), that if you made a bash_profile, it would work.

AFAIK Ubuntu doesn`t have a .bash_profile

You put you aliases in .bashrc

Why? .....

.....it must have seemed like a good idea at the time (to the ubuntu devs)

Yes, if you are following a general bash tutorial, this is not helpful to you :)

I await flaming.

---

### Post by Tawrtoise on 2010-10-14
Even after putting the aliases at the bottom of .bashrc they don't work? When exactly are these supposed to run?

---

### Post by Sub101 on 2010-10-14
They should run/load whenever you open a new terminal

---

### Post by nothingspecial on 2010-10-14
> **nothingspecial said:**
> 

```
. ~/.bashrc
```


Don`t forget that bit :)

---

### Post by Tawrtoise on 2010-10-14
> **Sub101 said:**
> They should run/load whenever you open a new terminal

What kind of permissions am I supposed to have?
Mine is set to rw-r--r--r

Also, the only aliases I've added are:

```
Alias l='ls -l'
Alias today='date +"%A, %B %-d, %Y"'
```

---

### Post by Sub101 on 2010-10-14
> **Tawrtoise said:**
> What kind of permissions am I supposed to have?
Mine is set to rw-r--r--r

Also, the only aliases I've added are:

```
Alias l='ls -l'
Alias today='date +"%A, %B %-d, %Y"'
```

Alias needs to be little a. So;

```
alias l='ls -l'
alias today='date +"%A, %B %-d, %Y"'
```

---

### Post by Miyavix3 on 2010-10-14
To be honest, it's nicer to have a separate file for aliases.

First type```
gedit .bashrc
```
so we can add these lines:
```

if [ -f ~/.bash_alias ]; then
    . ~/.bash_alias
fi

```

That will tell your terminal to look for a file named .bash_alias every time it opens. That means after you do all this stuff, you will have to close your current window and open a new terminal.

Then open up gedit and write your aliases in there. Save it as .bash_alias in your home directory. And you're done!

---

### Post by Tawrtoise on 2010-10-15
> **Miyavix3 said:**
> To be honest, it's nicer to have a separate file for aliases.

First type```
gedit .bashrc
```so we can add these lines:
```

if [ -f ~/.bash_alias ]; then
    . ~/.bash_alias
fi

```That will tell your terminal to look for a file named .bash_alias every time it opens. That means after you do all this stuff, you will have to close your current window and open a new terminal.

Then open up gedit and write your aliases in there. Save it as .bash_alias in your home directory. And you're done!

Does that need to go at the bottom of .bashrc?

---

### Post by nothingspecial on 2010-10-15
> **Tawrtoise said:**
> Does that need to go at the bottom of .bashrc?


It can go where you like, except don`t put it in the middle of an if statement. A bit that starts with if and ends with fi.

I`d just put it at the bottom.

---

### Post by Tawrtoise on 2010-10-15
> **nothingspecial said:**
> It can go where you like, except don`t put it in the middle of an if statement. A bit that starts with if and ends with fi.

I`d just put it at the bottom.

Okay, that made it work. Thanks very much for the help every one.

---

### Post by VMC on 2010-10-15
> **Miyavix3 said:**
> To be honest, it's nicer to have a separate file for aliases.

First type```
gedit .bashrc
```
so we can add these lines:
```

if [ -f ~/.bash_alias ]; then
    . ~/.bash_alias
fi

```

That will tell your terminal to look for a file named .bash_alias every time it opens. That means after you do all this stuff, you will have to close your current window and open a new terminal.

Then open up gedit and write your aliases in there. Save it as .bash_alias in your home directory. And you're done!

This is exactly how I've done mine. That file can be named anything , but since ".bash_alias" has been recommended that's what I used.

---

