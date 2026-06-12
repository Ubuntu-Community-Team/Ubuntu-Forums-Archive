---
title: "help editing a file."
date: 2010-03-13
forum: General Help
---

### Post by sincerelyydavid on 2010-03-13
do you need a # in front of a command when editing a file on your computer?

---

### Post by n0dix on 2010-03-13
I don't understand what you want to do? Can you be more specific?

---

### Post by carandraug on 2010-03-13
> **sincerelyydavid said:**
> do you need a # in front of a command when editing a file on your computer?

Sorry but your question makes no sense whatsoever. I'm not sure what you mean but considering half of your question, I'll answer to the question (still not very good)

"Do you need a # at the start of a line when editing a file on your computer?"

Some files of your computer are configurationf iles for programs. In most cases, you can comment some lines of the file by adding the character # at the start of said line. This will make the program to ignore that line. This is useful, for example, to add an explanation what the following lines do which makes the file easier to read by the user.

---

### Post by Villiam on 2010-03-13
For that matter I know that in Java and many other programming language for commenting we use slash: /
Until you are more specific, lets keep it that way.

---

### Post by n0dix on 2010-03-13
> **Villiam said:**
> For that matter I know that in Java and many other programming language for commenting we use slash: /
Until you are more specific, lets keep it that way.

You mean, double slash: //  or /* */ for more than one line.

---

### Post by howefield on 2010-03-13
> **sincerelyydavid said:**
> do you need a # in front of a command when editing a file on your computer?

You can edit any of the files in your home folder without admin privileges, to edit anything outside your home folder you would to gain need admin privileges by preceding the command with sudo or gksudo.

As others have said, be a bit more explicit for more help.

---

### Post by carandraug on 2010-03-13
> **Villiam said:**
> For that matter I know that in Java and many other programming language for commenting we use slash: /
Until you are more specific, lets keep it that way.

> **n0dix said:**
> You mean, double slash: //  or /* */ for more than one line.

My guess is that if he's asking about editing Java, C or any code files then he'd knew better than make this question. If he's indeed asking about commenting files, it's probably configuration files like grub (specially if you search for his other threads). It's on my previous reply the expression "in most cases" which I believe stands true for configuration files (it's also explicit on my previous answer that I'm only talking about them).

---

### Post by sincerelyydavid on 2010-03-14
alright, so i'm editing /etc/sysctl.conf and want to add the line "vm.swappiness=10" at the very end of the document. do i need to add a "#" before vm.swappiness=10.
so
vm.swappiness=10
or
#vm.swappiness=10

---

### Post by Slim Moe on 2010-03-14
# identifies a comment - everything behind it will be ignored.

---

### Post by n0dix on 2010-03-14
The '#' character at the start of a line means that line is ignored to the process.

---

