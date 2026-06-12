---
title: "Was my folder name interpreted as a command?"
date: 2011-07-25
forum: General Help
---

### Post by kevjonesin on 2011-07-25
Hello,

   I'm confused by terminal's response to my input. I'm running Lucid (10.04 LTS) Desktop at present.

[IMG]http://4.bp.blogspot.com/-9pNfusOj_BA/Ti3IewGDY2I/AAAAAAAAAB0/2gpXaek3JlQ/s320/terminal-puzzle.png[/IMG]

Why did "me@ibme-puter:~/Software$" become ">", as opposed to "me@ibme-puter:~/Software/OS's$ when I used the "cd" command again?

Was the the punctuation in folder "OS's" the cause?

Is ">" some kinda' new (to me) shell? Thought it best to ask.

   : }

---

### Post by GWBouge on 2011-07-25
Yeah, it's assuming the ' is a quote, and brings up the > like you're not done with the command (you never ended your quote, after all ...).  To cd to that effectively, you'll have to either quote the name, or escape the ', so it knows to treat it as part of the folder name:

```
$ cd "OS's"
$ cd OS\'s
```

---

### Post by kevjonesin on 2011-07-25
Thanks, 

cd "OS's" 

...got me where I wanted to be.

   I'm curious, does "\" simply tell terminal to ignore the next character? What is it's usage/purpose in general?

---

### Post by Habitual on 2011-07-25
"cd O" +[tab] works really well in such cases. :)

---

### Post by GWBouge on 2011-07-25
Escape Character: [http://en.wikipedia.org/wiki/Escape_character]("http://en.wikipedia.org/wiki/Escape_character")

Pretty much just tells the terminal (or programming language) to treat the character following it as part of the string, instead of it's typical function within the command.  Also used to represent special characters, such as "\n" for newline or "\t" for a tab.

---

### Post by kevjonesin on 2011-07-25
Thanks y'all,

):P

---

