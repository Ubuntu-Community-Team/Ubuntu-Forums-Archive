---
title: "disown doesn't have a man page"
date: 2011-09-02
forum: General Help
---

### Post by flickerfly on 2011-09-02
I've tried to go through the bug reporting process (when did that get so complicated?) and became mired down in trying meet the requirements for reporting this simple bug. If you can do it, feel free to do it and take all the credit.

disown does not have a man page. A copy of one can be found here if it is applicable.
[http://www2.research.att.com/~gsf/man/man1/disown.html](http://www2.research.att.com/~gsf/man/man1/disown.html)

I wondered if this was just the way of it with all bash built-in commands. bg, jobs and fg are missing man entries however wait and kill do have them.

Whatever the case, this is inconsistent and probably should be resolved.

---

### Post by haqking on 2011-09-02
> **flickerfly said:**
> I've tried to go through the bug reporting process (when did that get so complicated?) and became mired down in trying meet the requirements for reporting this simple bug. If you can do it, feel free to do it and take all the credit.

disown does not have a man page. A copy of one can be found here if it is applicable.
[http://www2.research.att.com/~gsf/man/man1/disown.html]("http://www2.research.att.com/%7Egsf/man/man1/disown.html")

I wondered if this was just the way of it with all bash built-in commands. bg, jobs and fg are missing man entries however wait and kill do have them.

Whatever the case, this is inconsistent and probably should be resolved.

Write your own

[http://tldp.org/HOWTO/Man-Page/](http://tldp.org/HOWTO/Man-Page/)

---

### Post by dave01945 on 2011-09-02
i think that is because it is a shell built in command and it is covered in the man page for bash

---

### Post by haqking on 2011-09-02
> **dave01945 said:**
> i think that is because it is a shell built in command and it is covered in the man page for bash

+1

man bash and in the shell built in commands section.

or like i said above write your own ;)

---

### Post by flickerfly on 2011-09-02
I already anticipated and addressed both these responses in the original comments.

bash built-ins either should or shouldn't be included in man, not both. It should be consistent. Since it is very unclear that they are built-in, I vote that they should be documented on their own.

A man page already exists for disown, it simply isn't in place. There is no need to write one.

---

### Post by sisco311 on 2011-09-02
```
man bash | less +/"^ +disown"
```

or use help to display info about the built-ins:
```
help disown
```

---

### Post by sisco311 on 2011-09-02
> **flickerfly said:**
> 
I wondered if this was just the way of it with all bash built-in commands. bg, jobs and fg are missing man entries however wait and kill do have them.


/bin/kill is not the same as the kill built-in. If you read its man page you will see:
> 
NOTES
       Your shell (command line interpreter) may have a built-in kill com&#8208;
       mand.   You may need to run the command described here as /bin/kill
       to solve the conflict.


;)

The same applies to wait, test, [ and so on.

> **flickerfly said:**
> 
Whatever the case, this is inconsistent and probably should be resolved.

The shell built-ins are documented in the shell's man page. bash also has a help built-in.

Commands are documented in their man page.

HTH

---

### Post by flickerfly on 2011-09-02
Ah, thanks Sisco311. So it is consistent, just confusing.

---

### Post by AlphaLexman on 2011-09-02
If you wrote your own manpage, or even copied the one from your link, you can use a special variable to tell where extra man pages are: [http://manpages.ubuntu.com/manpages/dapper/man1/manpath.1.html](http://manpages.ubuntu.com/manpages/dapper/man1/manpath.1.html)

---

