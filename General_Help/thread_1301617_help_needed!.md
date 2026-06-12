---
title: "help needed!"
date: 2009-10-26
forum: General Help
---

### Post by hifza on 2009-10-26
[SIZE=2]im completely new to linux. i have the following task to complete. i managed to do this by adding aliases to the .bashrc file and by changing the PS format from there. but the teacher wants it all to be done in the form of a c code. plz help.[/SIZE]

[FONT=Arial][SIZE=2]_TASK:_
[/SIZE][/FONT][FONT=Arial][SIZE=2]When the process starts, a prompt of following format should appear on the Terminal/Konsole:  [/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]**[time] user@host: working_dir $ **[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]**e.g., [12:34] ali@myPC: /home/ali $ **[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]Students are required to implement three possible operations. These include[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] [FONT=Arial][SIZE=2]When the user enters “**list**”,     a listing of all the contents of the working directory should be     displayed (similar to the '**ls**' program in Linux)[/SIZE][/FONT]
     [FONT=Arial][SIZE=2]When the user enters “**create**     *file_name content*”, the process should[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Create a file called *file_name *in     the current directory[/SIZE][/FONT]
     [FONT=Arial][SIZE=2]Write the string “*content*” into the newly created     file[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]The process should terminate/end     when the user enters "**quit**"[/SIZE][/FONT]

---

### Post by dvlchd3 on 2009-10-26
I'm not sure if this will be considered cheating by your teacher, however, you can include the cstdlib header, and use they system() function to execute system commands.

Examples:

```

system("ls");   // List current files/directories in working directory
system("pwd");  // Get the current working directory

```

Not sure what the system function technically takes as its parameters, but I believe you can build some sort of string outside to create the file.

I believe the command would look something like this:
```

echo "content" > file_name

```

Hope this helps, perhaps someone else may be able to offer an easier/more efficient solution.

---

### Post by QLee on 2009-10-26
[QUOTE=hifza][SIZE=2]im completely new to linux. i have the following task to complete. i managed to do this by adding aliases to the .bashrc file and by changing the PS format from there. but the teacher wants it all to be done in the form of a c code. plz help.[/SIZE]
[/QUOTE]

hifza, you're probably going to find that many of the people here who could help will be reluctant to do your homework for you (or a moderator might lock your thread), on the other hand, if you make a try at it and post what you think might work, many might be willing to point out errors for you or make suggestions. If you annotate your code with the why for each step, it would make the homework even better.

---

### Post by shadow120 on 2009-10-26
> When the user enters &#8220;list&#8221;, a listing of all the contents of the working directory should be displayed (similar to the 'ls' program in Linux)

ls -lac

> When the user enters &#8220;create file_name content&#8221;, the process should

touch file_name

or to create file with content in it

echo "content" > file_name


also this is "the one page linux manual" pdf  [www.digilife.be/.../The%20One%20Page%20Linux%20Manual.pdf](www.digilife.be/.../The%20One%20Page%20Linux%20Manual.pdf)

---

### Post by hifza on 2009-10-26
> **QLee said:**
> hifza, you're probably going to find that many of the people here who could help will be reluctant to do your homework for you (or a moderator might lock your thread), on the other hand, if you make a try at it and post what you think might work, many might be willing to point out errors for you or make suggestions. If you annotate your code with the why for each step, it would make the homework even better.

it is my first time using linux, it would be an understatement to say i'm a little lost.
as i said, i searched a lot, and managed to do this with aliases in the .bashrc file, and as i said, that's not what was needed.

isn't there a way i could add the same thing to a new bash script and somehow call that from the c code so that it still performs all the required functions?

---

