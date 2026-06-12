---
title: "Terminal - .bash_profile not changing/taking effect"
date: 2012-02-13
forum: General Help
---

### Post by Rebant on 2012-02-13
I'm trying to change PATH by using the .bash_profile.
This is what I have in it right now:
```
export PATH=${PATH}:/home/supervisor/altera/bin
```
But when I type in "quartus" (the application I want to use which is in the path specified above), it doesn't work and my PATH variable is still not changed.

Isn't this file the one I need to change so I can get my terminal to do this every time I launch an instance of it?

Also, I thought that it was the .bash_profile file which caused the "rvm_env_string: command not found" thing to appear on my terminal (see pic).
[IMG]http://dl.dropbox.com/u/2792692/Terminal.png[/IMG]
This is because my .bash_profile originally had the following in it:
```
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function
[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function
```

Any help would be appreciated!

---

### Post by MG&amp;TL on 2012-02-13
I set my $PATH, and fiddle with other settings, via .bashrc, not .bash_profile. I've no idea whether that will work or not, but I would put back whatever *was* in that file before doing anything else.

---

### Post by HiImTye on 2012-02-13
make sure that you don't have it as your path already:
```
echo $PATH
```
if it isn't what youre trying to set it to then add the following to your .bashrc file:
PATH=$PATH:/home/supervisor/altera/bin

if it is already there, then it is likely a file permissions problem

---

### Post by Rebant on 2012-02-13
I had already tried to do what you said but it doesn't work.
That meaning, it works for the current window (instance of terminal) but when I open another one, the PATH variable is reset. :'(

I want it to be static so I don't have to edit the variable every time I open up the terminal.
With that said, what/where is the .bashrc file?

---

### Post by Rebant on 2012-02-13
> **Rebant said:**
> I had already tried to do what you said but it doesn't work.
That meaning, it works for the current window (instance of terminal) but when I open another one, the PATH variable is reset. :'(

I want it to be static so I don't have to edit the variable every time I open up the terminal.
With that said, what/where is the .bashrc file?

Never mind! Found it - and that did the trick!
Thanks.

---

