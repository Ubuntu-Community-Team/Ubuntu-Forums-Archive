---
title: "Remove all files from directory except some"
date: 2010-01-31
forum: General Help
---

### Post by lud on 2010-01-31
Hi Guys,

I am still a novice with Ubuntu and I am trying to write a shell script which will clean redundant files.

I am stuck with one line where I would need a command which will remove all files from directory except some of them. Can anyone please advice how to add such an exception to the **rm** command?

I have searched some bash shell tutorials, however, no joy. Guess I have overlooked something.

Thank you.

---

### Post by paxxus on 2010-01-31
One way is to use the find command, for example:

```
find . -maxdepth 1 -type f \! \( -name "A" -o -name "B" \) -delete
```This command finds all files in the current directory (.) and deletes all regular files (-type f) not named "A" or "B". The -maxdepth parameter ensures that find doesn't descend into sub-directories and deletes stuff.

The -name parameters may contain wildcards, e.g -name "tmp*".

The back-slashes are needed because some of the characters in the find expression are also interpreted by the shell, so you'll have to excape them with the \.

Have fun, and experiment in a test-directory before you delete left and right :)

Edit: Oh, and the -o means OR - I only put this in the example in case simple wildcarding isn't enough for you.

---

### Post by amac777 on 2010-01-31
For example, to remove all files _**in the current directory**_ except the ones that start with the letter 'a', use:
```

rm [!a]*
```

That example was taken from, and there are more examples here:

[http://linux-journal.blogspot.com/2005/04/delete-all-files-in-directroy-except.html](http://linux-journal.blogspot.com/2005/04/delete-all-files-in-directroy-except.html)

---

### Post by lud on 2010-02-01
Hi Guys,
 
Paxxus, thank you for your post, the solution you propose is inspirative and interesting for me. I am really eager to try it out and experiment. Thank you.
 
Amac777, your ''rm [!a]* directory'' seems like it can be extended after a little thinking. Thank you.
 
Both of you have taught me a lot.
 
Once I find time to resolve this I will post it here in case you guys are interested.
 
I am just enjoying my time with Ubuntu :p
 
Cheers

---

### Post by lud on 2010-02-01
Paxxus, your suggestion works great! What I value the most are the  -maxdepth and -o parameters. I did not know about these. However, I am confused with the back-slashes. Why are there three? I thought they should be always in pairs. For example, if I would like to omit ! I would write \!\. Isn't it so? I was playing with those three back-slashes for a while but was not able to understand why exactly they are there.
Thank you.

---

### Post by lud on 2010-02-01
amac777, yours suggestions works fine, too. However, I was not able to figure out how to delete all files except two of them with your method. I have two files which I want to preserve: ''lock'' and ''unlock''.
This one works to delete all except lock:
```
rm [!lock]*
```
However, how should I amend command above to delete all files except ''lock'' and ''unlock''?
Thank you.

---

### Post by SecretCode on 2010-02-01
> **lud said:**
> However, I am confused with the back-slashes. Why are there three? I thought they should be always in pairs. ...Not quite - a single back-slash escapes the next character, and only the next character. Unlike quotes, which need an open and a close.

So to escape _(_ you write _\(_  ... or _"("_. To escape _(abc)_ you write _\(abc\)_ or _"(abc)"_.

> **lud said:**
> amac777, yours suggestions works fine, too. However, I was not able to figure out how to delete all files except two of them with your method. I have two files which I want to preserve: ''lock'' and ''unlock''.
This one works to delete all except lock:
```
rm [!lock]*
```
However, how should I amend command above to delete all files except ''lock'' and ''unlock''?
Thank you.

I think the find command, as posted by paxxus, is going to be simpler for you to follow ... plus you can run it first without a _-delete_ parameter, and it will just list the selected files. When you're comfortable, you can delete them.

---

### Post by amac777 on 2010-02-01
Hi Lud,

I'm very sorry. I should have tested the solution I wrote above because it does not work as I expected and the difference is huge and horrible. I just realized the "directory" part at the end has no effect for the rm command and that means the command must be run _in the directory itself_ and if you did what I said exactly you might have ended up deleting files in the wrong directory. I've now edited the above post to say you need to run that in the directory that contains the files you want to delete. (I ended up deleting files in my home directory due to that error when I tested it! Luckily I had backups.)

Anyway, running this command in the directory that has the files you want to delete:

```
rm !(lock|unlock)
```

will delete all files except for "lock" and "unlock" _in the current directory_.

But I now prefer Paxxus's solution above with one small change for safety. His solution is better because it allows you to specify the exact directory you want in the command instead of relying on being in the current directory. Just change the . to the directory:

```
find directory -maxdepth 1 -type f \! \( -name "lock" -o -name "unlock" \)
```

and if that lists all the files you want to delete, run it again with the -delete at the end

---

### Post by lud on 2010-02-02
Hi Amac777,

I am glad you had backup files of your home directory.

I am now able to understand Paxxus' solution.

However when I type
```
rm !(lock|unlock)
```

I receive this message from terminal:

```
bash: !: event not found
```

I have used some variations of your command, however, no joy. 

You guys have already solved my problem so I am marking this thread as solved. However, if I would be able to use

```
rm !(lock|unlock)
```

that would be just great.

Thank you all for your time and support.

---

### Post by amac777 on 2010-02-02
I just retested that command and worked fine. Are you sure you got the closing bracket in the right direction? If you type this "rm !(lock|unlock(" then you will get that error message you wrote. Here's how I tested it:

```
:~$ mkdir testing
:~$ cd testing
:~/testing$ touch 1 2 3 4 lock unlock hello
:~/testing$ ls
1  2  3  4  hello  lock  unlock
:~/testing$ rm !(lock|unlock)
:~/testing$ ls
lock  unlock
:~/testing$ 

```

---

### Post by geirha on 2010-02-02
You need to enable the shelloption extglob in order to use extended globs (like the !(lock|unlock)).

```
shopt -s extglob
echo !(lock|unlock)

```

See this for more information about extended globs: [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

Also, the «!: event not found» message can be quite annoying. It's something called history expansion in bash, that allows you to use ! to grab parts of previous commands into your current. If you put ```
set +H
``` at the end of your ~/.bashrc, you won't be bothered with those anymore.

---

### Post by lud on 2010-02-05
Yes, it seems I am getting the closing bracket in correct direction:

```

root@hp550:~/Desktop/test# ls
1  2  3  4  5  lock  partial  unlock  XX
root@hp550:~/Desktop/test# rm !(lock|unlock)
bash: !: event not found
root@hp550:~/Desktop/test# 

```

Like Geirha [wrote]("http://ubuntuforums.org/showthread.php?t=1395145&page=2"), it seems I will have  to enable the shelloption extglob in order to use extended globs. I am just trying to figure out how to set it on.

Furthermore, when I was searching for the enable  shelloption extglo I found very interesting [article]("http://stackoverflow.com/questions/635378/unable-to-remove-everything-else-in-a-folder-except-filea") regarding removing all files except one or some of them in directory.

Thank you.
Cheers

---

### Post by lud on 2010-02-05
Hi Gerha,

thank you for putting new light onto this issue.

I am just in the process of figuring out how to enable the shelloption extglob. This is what I receive:

```
root@hp550:~/Desktop/test# shopt -s extblog
bash: shopt: extblog: invalid shell option name
root@hp550:~/Desktop/test# 

```

However, thank you for the hyperlink you gave me. I will do some research to figure out what is wrong here. If I get stuck will post here a message.

Furthermore, when I was searching for the enable  shelloption extglob I found very interesting [article]("http://stackoverflow.com/questions/635378/unable-to-remove-everything-else-in-a-folder-except-filea") regarding removing all files except one or some of them in a directory.

Thank you for your time and energy.

---

### Post by lud on 2010-02-05
Hi Geirha,

this simple script has done the job:

```

#! /bin/bash
cd /root/Desktop/test
# had to enable extglob
shopt -s extglob
rm !(lock|unlock)
echo ***Cleaning Done***
```

Here is the output in terminal:
```
root@hp550:~/script# ./clean2.sh
rm: cannot remove `partial': Is a directory
rm: cannot remove `XX': Is a directory
***Cleaning Done***

```

This removed all files except lock & unlock. Great! Thank you.

---

