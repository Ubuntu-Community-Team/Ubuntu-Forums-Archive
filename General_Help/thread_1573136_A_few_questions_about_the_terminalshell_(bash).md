---
title: "A few questions about the terminal/shell (bash?)"
date: 2010-09-12
forum: General Help
---

### Post by oskarkv on 2010-09-12
Hey! I just installed ubuntu yesterday, and I have a few questions that are kind of hard to search google for. Note that I switched from Windows, and have very little Unix experience.

1) The directories in ~/ all start with capital letters, e.g. Downloads and Desktop. It is annoying to have to reach for the shift key all the time when using the terminal to do stuff in these directories. I tried to rename Downloads to downloads, but ubuntu created a new Downloads for me. Is there a way to rename these directories in a proper way?

2) If renaming the directories doesn't work then maybe there is a way to configure the terminal to be case-insensitive. So if I enter ~/down and press TAB it will autocomplete to ~/Downloads. Actually this would be useful regardless of question 1. Can this be done?

3) Let's say there are Downloads and Desktop in my home directory. I enter ~/D and hit TAB. Currently nothing will happen. What I want is for the terminal to autocomplete to ~/Desktop and if I hit TAB again to ~/Downloads. So basically I want it to remember what I typed and then go through the possibilities one by one as I hit TAB. Can this be done?

4) I've used FreeBSD a little and if you type a few letters in the terminal there and then press up, you go through only the commands that you entered previously that start with those few letters. Currently if I try that, the letters are ignored and I just get the previous command regardless of what it started with. Can I get the FreeBSD behavior?

---

### Post by dirty_harry on 2010-09-12
Wow, yesterday ubuntu, today bash, and tomorrow...

Answering your questions:
1.) you could make a symlink to directory -> [https://secure.wikimedia.org/wikipedia/en/wiki/Ln_Unix](https://secure.wikimedia.org/wikipedia/en/wiki/Ln_Unix)

2.) please check that your using bash, if so you should take a look at bash reference, and search for cdspell -> [http://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html#The-Shopt-Builtin](http://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html#The-Shopt-Builtin)

echo $SHELL     # shows you which one you're using
bash --version   # shows you which version of bash you're using

3.) & 4.)  sorry, don't know about that but bash manual would be my choice to search for a solution (maybe I search for it later)

---

### Post by Lukas666 on 2010-09-12
> **oskarkv said:**
> Hey! I just installed ubuntu yesterday, and I have a few questions that are kind of hard to search google for. Note that I switched from Windows, and have very little Unix experience.

1) The directories in ~/ all start with capital letters, e.g. Downloads and Desktop. It is annoying to have to reach for the shift key all the time when using the terminal to do stuff in these directories. I tried to rename Downloads to downloads, but ubuntu created a new Downloads for me. Is there a way to rename these directories in a proper way?

2) If renaming the directories doesn't work then maybe there is a way to configure the terminal to be case-insensitive. So if I enter ~/down and press TAB it will autocomplete to ~/Downloads. Actually this would be useful regardless of question 1. Can this be done?

3) Let's say there are Downloads and Desktop in my home directory. I enter ~/D and hit TAB. Currently nothing will happen. What I want is for the terminal to autocomplete to ~/Desktop and if I hit TAB again to ~/Downloads. So basically I want it to remember what I typed and then go through the possibilities one by one as I hit TAB. Can this be done?

4) I've used FreeBSD a little and if you type a few letters in the terminal there and then press up, you go through only the commands that you entered previously that start with those few letters. Currently if I try that, the letters are ignored and I just get the previous command regardless of what it started with. Can I get the FreeBSD behavior?

Can't you use a file manager for all those tasks?

[http://www.linuxlinks.com/article/20081224191928555/FileManagers.html](http://www.linuxlinks.com/article/20081224191928555/FileManagers.html)

---

### Post by WorMzy on 2010-09-12
I believe that Desktop needs the capital letter since I think Nautilus is hardcoded to automatically recreate it if it's missing, but you can change the others by editing ~/.config/user-dirs.dirs

You can try renaming Desktop there, but I don't think it'll work.

Oh, and zsh lets you press tab to autocomplete when there's more than one possibility. You have to press twice to start the cycle though, the first time you press it it gives you the list of possible names, second time gives you the first possibility from the list, third time gives you the second, etc.

zsh is in the repos.

---

### Post by oskarkv on 2010-09-13
Thank you! I will look in to these things when I have time.

---

### Post by WorMzy on 2010-09-13
If you try out zsh, read this: [http://www.gentoo.org/doc/en/zsh.xml](http://www.gentoo.org/doc/en/zsh.xml)

I've never found a version written for Ubuntu, but if you skip the parts that are specifically for gentoo then it's quite useful.

---

### Post by pbrane on 2010-09-13
CTRL+R in the bash shell will enable you to type a few letters to get that previous command. CTRL+R again to search through the selections.

About ~/Downloads vs. ~/downloads, I don't have ~/Downloads, I created a ~/downloads directory. But nautilus does not try to create a ~/Downloads dir on my system. I'm running a fresh install of Lucid. I'm not sure why yours would do that. Maybe some program (like firefox) is doing that?

---

### Post by WorMzy on 2010-09-13
It's not Nautilus that remakes ~/Downloads, it's [xdg-user-dirs]("http://freedesktop.org/wiki/Software/xdg-user-dirs"). If yours doesn't recreate the ~/Downloads folders, then either you don't have it installed, or you've altered the settings.

---

### Post by drewsavini on 2010-09-13
this may be more trouble that it's worth, but regarding the case-insensitive idea: have you considered creating aliases?  you'd have to create one for each folder, but i think it would work.  correct me if this is wrong, though.

---

