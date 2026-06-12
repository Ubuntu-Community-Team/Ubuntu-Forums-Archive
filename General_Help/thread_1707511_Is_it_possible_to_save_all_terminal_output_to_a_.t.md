---
title: "Is it possible to save all terminal output to a .txt file?"
date: 2011-03-15
forum: General Help
---

### Post by kansasnoob on 2011-03-15
I sometimes stick my neck out and provide somewhat detailed, and often risky, "Mr-fix-it" remedies for boot problems. Now, I know it's possible to amend each command with "whatever_command > whatever.txt" in which case it'll place the command output in a file in /home.

But if you're directing someone to run a lot of commands as I did [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10562947&postcount=31") is it possible to save the output of all commands to a .txt file without amending each command?

Or is it already saved somewhere that I'm not yet aware of? I wouldn't be surprised if the latter were true, I just haven't yet found it :)

Thanks in advance.

---

### Post by r-senior on 2011-03-15
How about using tee?

$ bash | tee logfile.txt

When you are finished, 'exit' to drop back to the original shell and your output should all be in logfile.txt.

---

### Post by Rubi1200 on 2011-03-15
Well, unless you have changed the defaults, all bash commands are saved in .bash_history in your home folder.

@r-senior: nice command, but that seems to save the actual output of the commands rather than the commands themselves. Not sure if that is what kansasnoob was looking for.

I suppose you could also do this perhaps?

```
 history > saved_commands.txt
```This will save commands used in the terminal into a text file.

The default number of saved commands is 1,000.

---

### Post by nothingspecial on 2011-03-15
Use script eg

```
script output.txt
```

When you are done press Ctrl-D

Then have a look 

```
less output.txt
```

See man script for details

---

### Post by kansasnoob on 2011-03-18
As I test and poke around more and more I'm finding that everything I'd want to see is in /var/log :)

Most likely either /var/log/apt/history.log or /var/log/apt/term.log so I'm now just playing with grep to see if I can use it with a "timestamp". Regardless it wouldn't be too ugly to ask for a copy of those entire logs since they're only text logs :)

So I'm marking this solved, thanks for the suggestions.

---

### Post by kaustubhvp on 2012-05-26
> **nothingspecial said:**
> Use script eg

```
script output.txt
```

When you are done press Ctrl-D

Then have a look 

```
less output.txt
```

See man script for details


worked perfectly according to the need!!!!:guitar:

---

### Post by oldos2er on 2012-05-26
Old thread closed.

---

