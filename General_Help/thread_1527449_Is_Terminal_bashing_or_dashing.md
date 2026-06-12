---
title: "Is Terminal bashing or dashing?"
date: 2010-07-09
forum: General Help
---

### Post by KonfuseKitty on 2010-07-09
I want to automate some tasks with shell scripts, but after some reading, I'm more confused than when I started.  Answers to the following questions would be greatly appreciated:

1. What is the difference between the "default shell" and the "login shell"?  I've read that Ubuntu 6 changed the default shell from bash to dash, but the login shell remained bash.
2. In my Ubuntu 10.04, when I open the Terminal, which shell am I using by default?
3. If I wanted to change the Terminal shell from one to the other, how would I do that?
4. When I read man pages for commands in the Terminal or access their "--help" option, for which shell is the explanation written, bash or dash?

Cheers to all the helpers! :)

---

### Post by jwbrase on 2010-07-09
> **KonfuseKitty said:**
> I want to automate some tasks with shell scripts, but after some reading, I'm more confused than when I started.  Answers to the following questions would be greatly appreciated:

1. What is the difference between the "default shell" and the "login shell"?  I've read that Ubuntu 6 changed the default shell from bash to dash, but the login shell remained bash.

dash is the default shell for the system to execute scripts with. /bin/sh is a symbolic link pointing to /bin/dash.

bash is the default shell for users interacting with the System.

> 
2. In my Ubuntu 10.04, when I open the Terminal, which shell am I using by default?

You're using bash.

> 
3. If I wanted to change the Terminal shell from one to the other, how would I do that?

Temporarily or permanently?

For just the current terminal and session, just the name of the shell you want will do, or "exec nameOfShell" to stop running the current shell before starting the new one. 

If you want to permanently change what shell gets started when you open up a terminal window or login to a console, "usermod -s /path/to/shell yourUserName".

> 
4. When I read man pages for commands in the Terminal or access their "--help" option, for which shell is the explanation written, bash or dash?

Cheers to all the helpers! :)

Commands that have individual manpages exist somewhere on your system as standalone executables that behave the same way no matter what shell you execute them from. However, it is possible that your shell has a built-in version of the same command that it executes instead. In that case the shell built-in version will be described on the shell's manpage, not the command's.

---

### Post by bodhi.zazen on 2010-07-09
An alternate method of changing shells is with the chsh command.

```
chsh
```

It is unlikely you would want to use the dash shell. If you are wanting an alternate to bash, consider zsh.

---

### Post by KeyserSoze93 on 2010-07-09
They didn't change bash to dash. What they did was to make the shell "sh" (used by some scripts) point to dash instead.

Your interactive shell is bash (or whatever is specified in /etc/passwd.) Your shell scripts should begin with #!/bin/bash, instead of #!/bin/sh, to ensure they are executed with the right shell.

Alternatively, you can run:

```

sudo rm /bin/sh &&
sudo ln -s /bin/bash /bin/sh

```

Just be careful to enter it right. This will make /bin/sh point to bash, for any old scripts etc. which expect it to do so.

---

### Post by KonfuseKitty on 2010-07-09
Thanks for the explanations!  I take it I'm basically safe using bash, I just need to be sure to properly point to it.

The only outstanding issue that I can see is scripts downloaded from the internet and using "bin/sh".  I guess the only way to be sure whether the author is pointing to bash or dash would be to examine the script, something not so easy for a newbie to do.  Then again, a newbie probably shouldn't be using scripts from the internet anyhow, so no big deal.

---

### Post by kaibob on 2010-07-09
> **KonfuseKitty said:**
> I want to automate some tasks with shell scripts, but after some reading, I'm more confused than when I started. <snip>

Your questions have been answered by the other forum members, but I thought I would add one point. You state that you want to automate some tasks with shell scripts. That being the case, you can use bash or dash or whatever shell you want. Just use the applicable shebang in your script.

Most Ubuntu users seem to use bash, but there are circumstances where dash might be applicable. Probably the primary reason is efficiency. For example, my computer is old and quite slow, so, whenevery possible, I use dash in my shell scripts. 

You may have seen the following, but it explains some of the differences between dash and bash:

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

Because you are new to shell scripts, you may want to stick with bash for now. The differences between bash and dash are not great, but they can be a source of confusion initially.

---

### Post by mcduck on 2010-07-09
> **KonfuseKitty said:**
> Thanks for the explanations!  I take it I'm basically safe using bash, I just need to be sure to properly point to it.

The only outstanding issue that I can see is scripts downloaded from the internet and using "bin/sh".  I guess the only way to be sure whether the author is pointing to bash or dash would be to examine the script, something not so easy for a newbie to do.  Then again, a newbie probably shouldn't be using scripts from the internet anyhow, so no big deal.

As Dash is able to handle everything the original Sh shell did, any script that defines it's shell as /bin/sh should execute just fine using Dash.

If you make a script that needs Bash-specific features you'd point it to /bin/bash instead. Same goes for any other shell, if you make a script that uses fish, you specify /bin/fish in your script.

Of course you *might* run into some script made by somebody who didn't bother with specifying the correct shell even though the script isn't sh-compatible, but you'll definitely get an error message that tells you so when you try to execute the script. Luckily that isn't very common, most people write their scripts correctly. And even if that happens all you need to do is change the shebang on the first line of the script to point to correct shell.

---

### Post by Simian Man on 2010-07-09
> **KeyserSoze93 said:**
> They didn't change bash to dash. What they did was to make the shell "sh" (used by some scripts) point to dash instead.

I learned that the hard way when I tried to run some scripts on an Ubuntu computer :(.

---

### Post by mcduck on 2010-07-09
> **Simian Man said:**
> I learned that the hard way when I tried to run some scripts on an Ubuntu computer :(.

It might be a good idea to keep your scripts sh-compatible, or use the correct shebang if you want to use some extra features other shells might have.

Personally, I've never actually done any script that would *really* require any Bash-specific features. So I don't use such features and all my scripts will run on any sh-compatible shell, be it Bash or Dash or some other. :)

edit: I just wanted to add that because I keep my scripts sh-compatible I can actually execute them with Dash instead of Bash even though I use Bash as my login shell, and doing that gives a noticeable performance boost for any even reasonably complex script.

---

### Post by Simian Man on 2010-07-09
> **mcduck said:**
> It might be a good idea to keep your scripts sh-compatible, or use the correct shebang if you want to use some extra features other shells might have.

Yes you are right, but it's not only a question of "bash specific features"; dash is a lot pickier about lots of things than bash is.  My scripts were failing on strange things like string comparisons with cryptic errors.

---

