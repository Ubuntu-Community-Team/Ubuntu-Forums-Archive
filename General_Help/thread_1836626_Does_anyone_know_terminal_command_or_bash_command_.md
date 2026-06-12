---
title: "Does anyone know terminal command or bash command to copy  and paste"
date: 2011-08-31
forum: General Help
---

### Post by jolian ramos on 2011-08-31
Does anyone know terminal command or bash command to copy text from a file , and paste it in another file ?

---

### Post by Habitual on 2011-08-31
cat file1 > file2

---

### Post by jolian ramos on 2011-08-31
ok ,but if i want to copy from a file to a terminal , will this command work too or there is another command ?

---

### Post by nothingspecial on 2011-08-31
Are you running X or is this console only?

Do you want to copy a whole file or just part?

Do you have a mouse or track pad you could use?

One gotcha is that the copy and paste shortcuts for a terminal are Ctrl-Shift-C and Ctrl-Shift-V

---

### Post by jolian ramos on 2011-08-31
i want to copy part from a file text ,then paste them to another opened terminal window ,doing this operation through another terminal windows where i will write my commands in it 

i hope i am abundantly clear now 

> **nothingspecial said:**
> Are you running X or is this console only?

Do you want to copy a whole file or just part?

Do you have a mouse or track pad you could use?

One gotcha is that the copy and paste shortcuts for a terminal are Ctrl-Shift-C and Ctrl-Shift-V

---

### Post by Wim Sturkenboom on 2011-08-31
> **jolian ramos said:**
> i hope i am abundantly clear nowNot really. we still don't know if you can use something like a mouse :D If so, read on for nothingspecial's last line in post #4

> **nothingspecial said:**
> One gotcha is that the copy and paste shortcuts for a terminal are Ctrl-Shift-C and Ctrl-Shift-V

---

### Post by nothingspecial on 2011-08-31
If you want to copy and paste in the console (no X), use screen. Install it and run it. 

Open another window Ctrl-A then C

Open file 2 in that window

```
nano /path/to/file2
```

go back to the first window Ctrl-A then 0 (zero not capital o)

Open file 1 in that window

```
nano /path/to/file1
```

Enter screen's copy mode Ctrl-A then [


Use your arrows to place the cursor at the begining of the text then press space. Then use the arrows to highlight the text and press space again.

Then move to file 2 Ctrl-A then 1

Then paste Ctrl-A then ]

Simple :-\"

---

### Post by jolian ramos on 2011-08-31
> **Wim Sturkenboom said:**
> Not really. we still don't know if you can use something like a mouse :D If so, read on for nothingspecial's last line in post #4
i knew about the invention called mouse and i have one of it with me , but the matter is there is a part of text file i want to copy and paste it five times to open tapped terminal so instead of paste five time or more( according to number of tapped terminal i will open in future ) . i want to know command , which can do the copy and paste operation to put it in bash script , and it does  the past for me .

---

### Post by bodhi.zazen on 2011-08-31
> **jolian ramos said:**
> i knew about the invention called mouse and i have one of it with me , but the matter is there is a part of text file i want to copy and paste it five times to open tapped terminal so instead of paste five time or more( according to number of tapped terminal i will open in future ) . i want to know command , which can do the copy and paste operation to put it in bash script , and it does  the past for me .

copy - paste is managed through X so there is not an easy series of commands to manage this for you.

You must still select the text with your mouse and then paste it somewhere. These are mouse and/or keyboard events.

copy - paste functionality is responding to user input, not a bash script.

With that said, you can take a look at xsel , but I do not think that is what you are looking for.

On the command line you are looking at tools such as grep, sed, awk, perl ...

One or more of the above tools should do the trick for you.

---

