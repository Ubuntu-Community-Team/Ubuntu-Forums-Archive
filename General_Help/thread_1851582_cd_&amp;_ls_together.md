---
title: "cd &amp; ls together"
date: 2011-09-28
forum: General Help
---

### Post by lolium on 2011-09-28
I use alot of aliases to make using ubuntu alot easier when i SSH in. Is there a way to merge the two together?
The method i was thinking of was creat alias of cdl and set it to "cd $path_typed; ls -l" But i wasnt sure how i could send in the variable simply, or is there a current way to do this?

Thanks in advanced

Sam

---

### Post by sisco311 on 2011-09-28
Use a function:
```
cdl (){
    cd "$@" && ls -l
}
```

[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions)

---

### Post by lolium on 2011-09-28
Sorry if this sounds utterly stupid, but how would i implement this into my .profile?

Regards

Sam

---

### Post by sisco311 on 2011-09-28
Simply copy and paste it at the and of the file. Assuming that you are using bash, you should put your aliases and functions in ~/.bashrc

~/.profile is only executed for login shells.

See: [http://mywiki.wooledge.org/DotFiles](http://mywiki.wooledge.org/DotFiles)

---

### Post by dave01945 on 2011-09-28
also if you create a file called

```
~/.bash_aliases
```

you can add your aliases in there that is sourced from **~/.bashrc** and this way it keeps the bashrc tidier especially if you add a lot of aliases

---

### Post by lolium on 2011-09-28
that doesnt appear to work, sorry for the late response
-bash: .bashrc: line 100: syntax error near unexpected token `)'
-bash: .bashrc: line 100: `(){
    cd  && ls -l
} '
Also I dont know if this is possible but is it possible to have it current .bashrc or .profile settings be taken over to a different linux? for example, at work i have many aliases setup for different scripts, is it possible to have them aliases take effect temporarily when i ssh to one of the servers?

Regards

Sam

---

### Post by dankdave on 2011-09-28
If you edit your ~/.bashrc file or ~/.bash_aliases, then you need to `source' them, or open a new terminal.  The terminal you used to edit that file will have `sourced' the old files, not the updated ones.

What happens when you type: 'source ~/.bashrc', and then try that command.

---

### Post by dankdave on 2011-09-28
> **dankdave said:**
> If you edit your ~/.bashrc file or ~/.bash_aliases, then you need to `source' them, or open a new terminal.  The terminal you used to edit that file will have `sourced' the old files, not the updated ones.

What happens when you type: 'source ~/.bashrc', and then try that command.

My apologies - please disregard the previous comment.

Remove the ` mark from your function.  It should simply be the text.  Then you can get away with typing something like 'cdl ~/Desktop/'

---

### Post by dankdave on 2011-09-28
> **lolium said:**
> 
Also I dont know if this is possible but is it possible to have it current .bashrc or .profile settings be taken over to a different linux? for example, at work i have many aliases setup for different scripts, is it possible to have them aliases take effect temporarily when i ssh to one of the servers?


Every time you ssh into a different computer, you will be using the shell dictated by that computer.  If you like common aliases, then you can simply copy your .bash_aliases file to all the computers you use.  If there are specific commands you'd like to run (this might be poor programming habit!  :o), then you could add a line to .bash_aliases such as 'source ~/.bash_aliaes_work', and add whatever work aliases you have to that new file.

Hopefully this helps!

---

### Post by lolium on 2011-09-28
Thank you guys, The problem was from trying to copy and paste it in which was causing the problem, and regarding the ssh query, that wouldnt be possible as at work we have thousands of servers so it wouldnt be fun going through each one and adding my own aliases, i dont think this would be permitted, so must likley this will not be possible im assuming?

Regards

Sam

---

