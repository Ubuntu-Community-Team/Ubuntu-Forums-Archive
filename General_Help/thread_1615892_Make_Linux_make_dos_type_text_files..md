---
title: "Make Linux make dos type text files."
date: 2010-11-07
forum: General Help
---

### Post by Cool Javelin on 2010-11-07
Can I get fp to output CR/LF as newline to text files rather then only LF?

Hello my fellow Linux friends:

I have a logging program creating text files on a Linux machine and want to see those files on another computer running DOS/Windows.

Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.

I understand I can convert the files using various methods (linux2dos, tr, etc...) but I would rather simply have the right (wrong?) format in the first place.

I have created the program in free pascal and that creates .txt files that are shared over the LAN and used by DOS.

I guess I can change every writeln statement to manually output the cr/lf, but I am hoping I can change an option in the compiler to do that for me.

Thanks,

Mark.

---

### Post by ajgreeny on 2010-11-07
Have a look at **man echo** in terminal.  I think that will give you what you want, ie **\n** instead of **CR/LF**, but sorry if I misunderstood your needs.

---

### Post by SaintDanBert on 2010-11-07
Give this page a read [http://www.cyberciti.biz/faq/howto-unix-linux-convert-dos-newlines-cr-lf-unix-text-format/](http://www.cyberciti.biz/faq/howto-unix-linux-convert-dos-newlines-cr-lf-unix-text-format/).

Writing "newline" instead of "crlf" is pretty deeply embedded in linux (*-nix) culture. The opposite is true for the win-doze world. Most folks who work with one foot in each world start with individual commands like those described in the article. If their needs expand, there are intra-networking and server tools that handle this conversion auto-magically.

Bonne chance,
~~~ 0;-Dan

---

### Post by TSJason on 2010-11-08
Optionally you could just convert the file to dos format when needed.

```
sudo apt-get install tofrodos
```

to find out the commands, just:

```
man tofrodos
```

---

### Post by Cool Javelin on 2010-11-08
Thanks all for your help,

ajgreeny, SaintDanBert, and TSJason, I do know about the file conversion methods, but these require either the one file working on one system at a time (convert in place) or, having 2 different files, (one outdated shortly) I was hoping to have only one file be shared.

ISaintDanBert, I know *nix uses newline, but I was hoping I could change the pascal compiler to make it output crlf. I doubt the generated Pascal program uses the *nix OS to add the newline to writeln statements, that must be in the compiler. I was hoping I could change the compiler.

I do have the source code for free pascal, maybe I will give it a look.

I did a grep of the writeln statements, in my Pascal program and see there aren't too many of them. It shouldn't be a difficult task to make each one output a CR as the last character and let Pascal add the LF.

Thanks again for your help.

---

