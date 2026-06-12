---
title: "What is this extra output from the set command?"
date: 2011-05-27
forum: General Help
---

### Post by The111 on 2011-05-27
I am learning Linux for a class, and I understand the set should list environment variables, however I have thousands of lines of text after those that appear to be code of some kind.  The professor says he does not know what it is and suspects I have a virus... which even as a total Linux noob, I doubt, since I was careful with my installation and usage procedures.

The file was too large to attach, so I have hosted it here:
[[COLOR=Blue]**_http://www.matthoover.com/set.txt_**[/COLOR]]("http://www.matthoover.com/set.txt")

Can somebody explain please?

Thanks.

---

### Post by sisco311 on 2011-05-27
In non-posix mode set also displays the functions. Most of the functions you see are used by bash-completion. bash completion extends bash's standard completion behavior to achieve complex command lines with just a few keystrokes.

In posix mode only shell variables are listed:
```
set -o posix
set
set +o posix
```

For more details, check out **man bash**. The set built in is explained at the SHELL BUILTIN COMMANDS section:
```
man bash | less +/"^SHELL BUILTIN COMMANDS"
```
;)
```
man bash | less +/"^ +set \[\-\-abefhkmnptuvxBCEHPT\]"
```

---

### Post by Smart Viking on 2011-05-27
Nothing to worry about, same happens with me.
EDIT: Great answer sisco311

---

### Post by The111 on 2011-05-27
Thank you sisco311.  I don't fully understand all that but I will research into it more later.  I just wanted to verify I did not indeed have a virus, as that suggestion bothered me.

---

### Post by sisco311 on 2011-05-27
You're welcome and don't worry. The output of *set* is normal and does not indicate that your system is infected by a malware.

In bash, by default, *set* lists the environment variables **and** the [bash functions]("http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions"). 

Most of the functions listed by *set* are used by bash to handle the [completion]("http://en.wikipedia.org/wiki/Command-line_completion") of different commands.

If you have any questions, please feel free to ask.

Oh, and if you are looking for a good bash guide, check out [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) alongside with the BashFAQ and BashPitfalls on the same page.

EDIT:

BTW, welcome to the forums!

---

