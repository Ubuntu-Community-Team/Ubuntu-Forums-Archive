---
title: "How do i edit my .bash_profile file?"
date: 2011-03-15
forum: General Help
---

### Post by btf18 on 2011-03-15
Hey there,

Can someone please tell me how to edit my .bash_profile file, so that i add a command: export PATH=$PATH:/home/bin so that this existing directory is added to my path for good? I dont know how to open the .bash_profile file. 

Thanks

---

### Post by andrew.46 on 2011-03-15
Simply use your favourite text editor, such as gedit. I have a similar setting but I will admit that my own is actually in *$HOME/.bashrc*, my *$HOME/.bash_profile* is as follows:

```

if [ -f $HOME/.bashrc ]; then
source $HOME/.bashrc
fi

```

Andrew

---

### Post by btf18 on 2011-03-15
Thanks Andrew, im not sure i understand your code as im new to scripting, but i do know how to use my text editor, Vim. Do i just type the code you said into Vim and that will open a file called .bash_profile? Then type the command i first said into that? Cheers

---

### Post by nothingspecial on 2011-03-15
I think Andrew is advising you to put you $PATH entry in ~/.bashrc instead.
```

vim ~/.bashrc
```

Put your path variable in that, then either log out and back in or get bash to read your new bashrc

```
. ~/.bashrc
```

---

### Post by btf18 on 2011-03-15
Instead of Andrews HOME would i type /home/bin? I just must have to type /home/bin into the code somehwere. Thanks guys. What does rc stand for? Whats the difference between Andrews way and the way the tutorial does it? Thank you

---

### Post by andrew.46 on 2011-03-16
> **btf18 said:**
> Instead of Andrews HOME would i type /home/bin? I just must have to type /home/bin into the code somehwere. Thanks guys. What does rc stand for? Whats the difference between Andrews way and the way the tutorial does it? Thank you 

Actually $HOME is a variable that will expand out to the correct path. Try the following command and it should all become clear:

```

andrew@skamandros~$ **[COLOR="Red"]echo $HOME[/COLOR]**
/home/andrew

```

rc files are for the most part configuration files, a nice read on the subject here:

Configuration file
[http://en.wikipedia.org/wiki/Configuration_file](http://en.wikipedia.org/wiki/Configuration_file)

As for the tutorial, can you give a link?

---

### Post by btf18 on 2011-03-16
Thanks Andrew. I want home/bin in my paths, will HOME just put home/username in my paths?

---

### Post by btf18 on 2011-03-16
Could you please tell me the exact code to type and where, remembering my directory to add to paths is /home/bin. thanks. This method is not the same as the tutorial does. And what is ./? It's always used to open files. i know its a directory. I know / is the root directory, but what does the . mean in ./? I just want to know how to edit my .bash_profile, I dont even know how to open my .bash_profile and view it. im confused as to the comments. Im new lol

---

### Post by btf18 on 2011-03-16
If i could just edit my .bash_profile to include the command in my first message. Thanks

---

### Post by andrew.46 on 2011-03-17
If you look a little further down in [the guide]("http://linuxcommand.org/wss0020.php") you have used you will see that the author of the guide also warns against use of PATH commands in $HOME/.bash_profile:

> 
Though placing your aliases and shell functions in your .bash_profile will work, it is not considered good form. There is a separate file named .bashrc that is intended to be used for such things.


and then goes on to give a variation of the condition that I suggested for your $HOME/.bash_profile.

Andrew

---

### Post by mcduck on 2011-03-17
> **btf18 said:**
> Thanks Andrew. I want home/bin in my paths, will HOME just put home/username in my paths?

So do you want /home/bin in the path, or $HOME/bin?

Two different things, the first one would be in the /home directory (/home/bin), the second one would be inside your user's home directory (/home/yourusername/bin).

..and the second one is *already included* in the path by default, if you just create the $HOME/bin directory.

And like it's already been said in this thread, there's no reason for you to use ~/.bash_profile, as there already are two configuration files that Ubuntu uses for this purpose, adding third one would just complicate things without any benefits. Use the ~/.bashrc or ~/.profile instead.

Actually if you take a look at ~/.profile, you'll find following lines, which add $HOME/bin to your path it it exists:
```
#set  PATH so it includes user's private bin if it exists
if [-d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

---

### Post by andrew.46 on 2011-03-17
> **mcduck said:**
> Actually if you take a look at ~/.profile, you'll find following lines, which add $HOME/bin to your path it it exists:
```
#set  PATH so it includes user's private bin if it exists
if [-d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

I was not aware of that, thanks for pointing this out :). The perils of posting to Ubuntu Forums while using another distro :(.

Andrew

---

### Post by btf18 on 2011-03-18
Im so new to this that im just confused, I will just need to get some more through my online tutorial to get to know it better, but, i wanted /home/bin in my paths and it is now, as i went into my .bashrc file via the GUI and added this line to the bottom: if [ -d /home/bin ] ; then
    PATH=/home/bin:"${PATH}"
fi

I want to do everything from the terminal/vim but im happy with just knowing this way for now as im so new and it will suffice as i have so much more important stuff to learn that i may as well move ahead with the tutorial.

Thanks a bunch guys.

---

### Post by btf18 on 2011-03-18
Thats also quite interesting that $HOME/bin will be in paths if it exists, which i dont think it does so if i were to create it, it would go in my paths. Thats good to know, thank you

---

### Post by btf18 on 2011-03-18
If anyone is still here, might you tell me what ~/ does in the termianl? i see you type it before many commands. Also, when i type ~/.bashrc, it says permission denied. What should ~/.bashrc do? should it open the file so i can edit it within the terminal? id be interested in doing that. 

Thanks

---

### Post by btf18 on 2011-03-18
bump

---

### Post by 5149.5 on 2011-03-19
Open a terminal; enter: cd. enter sudo vi .bashrc Make your changes. Save the changes and exit vi (Esc , wq, enter). Log off and log back in. In terminal; enter echo $PATH.

---

### Post by jerome1232 on 2011-03-19
> **5149.5 said:**
> Open a terminal; enter: cd. enter sudo vi .bashrc Make your changes. Save the changes and exit vi (Esc , wq, enter). Log off and log back in. In terminal; enter echo $PATH.

You should not need root privileges to edit a file in your home directory. Try just typing

```
nano ~/.bashrc
``` (of course you could change nano for vim, or pico or gedit, or whatever text editor pleases you)

the ~ symbol represents your home directory.

So if your user name was andrew then ~ would represent /home/andrew, ~/.bashrc would represent /home/andrew/.bashrc

---

### Post by btf18 on 2011-03-22
Thanks guys. Thats cleared up a lot for me.

---

