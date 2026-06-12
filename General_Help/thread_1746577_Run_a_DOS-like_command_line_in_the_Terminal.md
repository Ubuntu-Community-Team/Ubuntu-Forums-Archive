---
title: "Run a DOS-like command line in the Terminal"
date: 2011-05-01
forum: General Help
---

### Post by einir on 2011-05-01
I'm a relatively recent Linux convert and I'm studying computer science. I've been taking some time in getting myself familiar with the Terminal and the Linux command line and can now use the Terminal confidently, albeit with a little help from Google every now and then. I know that when I graduate and start working I will mainly be using Windows computers and thus I would like to be able to use the Windows Command Prompt confidently as well. 

Is there any way to run something in the terminal that mimics DOS behavior? If not, is there a possibility for me to personally configure an "alternate" terminal which only allows those linux commands that are equivalent to DOS commands, without removing any functionality of the "original" terminal?

I hope you get where I'm going with this.

---

### Post by Blasphemist on 2011-05-01
I'm looking because I know I recently saw what you're looking for. While doing this I have run into a couple things you might use.

[http://www.linuxnewbieguide.org/content/chapter-12-i-dont-know-any-commands](http://www.linuxnewbieguide.org/content/chapter-12-i-dont-know-any-commands)

The main page for that site is:
[http://www.linuxnewbieguide.org/](http://www.linuxnewbieguide.org/)

This includes instruction on converting dos batch files to shell scripts.
[http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/)

The bash manual.
[http://www.gnu.org/software/bash/manual/](http://www.gnu.org/software/bash/manual/)

Addison Berry has some good video's at Lullabot on using the command line.
[http://www.lullabot.com/about/team/addison-berry](http://www.lullabot.com/about/team/addison-berry)

Another learning the shell link.
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

This does have a small table of what you're looking for I think.
[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

This is a helpful command line tool for me.
[http://okiebuntu.homelinux.com/okwiki/clicompanion](http://okiebuntu.homelinux.com/okwiki/clicompanion)

And last but not least,
[http://www.tuxarena.com/static/intro_linux_cli.php](http://www.tuxarena.com/static/intro_linux_cli.php)

---

### Post by 5149.5 on 2011-05-02
[Cygwin]("http://goo.gl/MX63") is worth a look.

---

### Post by lykwydchykyn on 2011-05-02
You can run dosbox, which is a pretty good imitation of DOS (good enough to run most DOS software).  Or you can run FreeDOS in a virtual machine on very little resources.

But frankly, the windows command shell is more than just DOS; it doesn't have a lot of commands, but most of the important ones for Windows administration are unique to Windows and won't be found in DOS.

I'd say if you want to be proficient with Windows, you want to get yourself a copy of it and run it in a VM.  You'd want to learn powershell or vbscript to have any useful Windows scripting knowledge anyway.

---

### Post by DaithiF on 2011-05-02
> **einir said:**
> I know that when I graduate and start working I will mainly be using Windows computers and thus I would like to be able to use the Windows Command Prompt confidently as well. 

rather than try to work with the almost-useless windows command prompt, I would suggest you use the previously mentioned cygwin.  It is a great solution for those of us (myself included) forced to use windows at work.  It gives you a fully-functional bash shell and most of the common unix/linux command line utilities.  That way you do real scripting in a windows environment.

---

