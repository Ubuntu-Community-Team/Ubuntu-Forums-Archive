---
title: "Terminal becomes broke!? Just gets &gt; prompt"
date: 2010-04-27
forum: General Help
---

### Post by Cavsfan on 2010-04-27
I was using ffmpeg and mencoder making a video of some jpgs of my grandson when something weird happened.
I entered a chmod command and then all I got was ">" on the left side of the terminal.
I closed the terminal and reopened it and got back to where I was at and ended up with the same thing.
>
>
>
I can not enter exit or anything else. I just have to close it.
Rebooting didn't even help it. Now I cannot enter other commands like an ffmpeg command.
I was able to cd to where I wanted to go, but when I got there and tried about any command I ended up with a ">" prompt.

Is this a bug, or does anyone have any idea what happened?
Thank you!

---

### Post by andrew.46 on 2010-04-27
Hi Cavsfan,

Perhaps a quick look at ~/.bash_history might show the problem command?

Andrew

---

### Post by VMC on 2010-04-27
> **Cavsfan said:**
> I was using ffmpeg and mencoder making a video of some jpgs of my grandson when something weird happened.
I entered a chmod command and then all I got was ">" on the left side of the terminal.
I closed the terminal and reopened it and got back to where I was at and ended up with the same thing.
>
>
>
I can not enter exit or anything else. I just have to close it.
Rebooting didn't even help it. Now I cannot enter other commands like an ffmpeg command.
I was able to cd to where I wanted to go, but when I got there and tried about any command I ended up with a ">" prompt.

Is this a bug, or does anyone have any idea what happened?
Thank you!
That usually means an incomplete command. Ctrl+c should break the ">". Which is waiting for completion.

---

### Post by cariboo on 2010-04-27
This really is a Lucid specific problem. Moved to General Help.

---

### Post by Cavsfan on 2010-04-28
> **andrew.46 said:**
> Hi Cavsfan,

Perhaps a quick look at ~/.bash_history might show the problem command?

Andrew

I don't appear to have that directory in home or the log directory.
Thanks

> **VMC said:**
> That usually means an incomplete command. Ctrl+c should break the ">". Which is waiting for completion.
Thanks. I'll try it again. It could have been the command. I'll have to look at that more closely.

> **cariboo907 said:**
> This really is a Lucid specific problem. Moved to General Help.

I didn't know if Lucid problems were out of the test part of the forum, but I do now. Thanks!

---

### Post by gmargo on 2010-04-28
The "> " you were seeing is bash's secondary prompt, known as **PS2**.  (Search for PS2 in the **bash(1)** man page.)  Bash will give the secondary prompt if the command typed so far is incomplete.  While you can type multi-line bash commands (like if ... fi) using this feature, usually people see this due to unmatched quote characters.  Verify this by deliberately leaving off a closing quote.  Type the quote on the next line or any of the following PS2 prompt lines.  Or escape the PS2 prompt with Control-C or Control-D.
```

$ echo "Hello World
> 
> 
> 
> "
Hello World





```

---

### Post by Cavsfan on 2010-04-28
> **gmargo said:**
> The "> " you were seeing is bash's secondary prompt, known as **PS2**.  (Search for PS2 in the **bash(1)** man page.)  Bash will give the secondary prompt if the command typed so far is incomplete.  While you can type multi-line bash commands (like if ... fi) using this feature, usually people see this due to unmatched quote characters.  Verify this by deliberately leaving off a closing quote.  Type the quote on the next line or any of the following PS2 prompt lines.  Or escape the PS2 prompt with Control-C or Control-D.
```

$ echo "Hello World
> 
> 
> 
> "
Hello World

```

You people are good!

I got exactly what is above when I left off the right quote.
I pressed Ctrl C and it went right back. It must have been something I  did for sure.

I have been working on that video and am going to  have to give up for today. 
If the goals didn't keep changing, I might have gotten it, but when they move on you, you never know.

Thanks to everyone that replied for the info and I will resolve this thread! 
Have a great day/night!!! :smile:

---

