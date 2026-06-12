---
title: "Terminal command to list disk usage in order?"
date: 2010-03-29
forum: General Help
---

### Post by cAlpha on 2010-03-29
I regularly use 'df -h' to check usage on each of my primary directories and mount points.  

I'm currently somewhat confused by disk usage within my filesystem, so I'd like to do the following:

Display directory size of all, or say, the 10 largest, subdirectories to a specified directory.  So, if I passed the root (/) directory, output would list the subdirectory of / with the largest disk usage first and its associated disk usage listed in human readable format (either M or G suffix as appropriate), followed by the subdirectory and usage for the second largest directory and so on.  

Can anyone suggest a command or series of commands to do this?

---

### Post by cjhabs on 2010-03-29
> **cAlpha said:**
> I regularly use 'df -h' to check usage on each of my primary directories and mount points.  

I'm currently somewhat confused by disk usage within my filesystem, so I'd like to do the following:

Display directory size of all, or say, the 10 largest, subdirectories to a specified directory.  So, if I passed the root (/) directory, output would list the subdirectory of / with the largest disk usage first and its associated disk usage listed in human readable format (either M or G suffix as appropriate), followed by the subdirectory and usage for the second largest directory and so on.  

Can anyone suggest a command or series of commands to do this?

How about:

```

du -k -S / | sort -g -r

```

---

### Post by cAlpha on 2010-03-29
> **cjhabs said:**
> How about:

```

du -k -S / | sort -g -r

```


Thanks for your reply.  It looks like the -h option works the same for du as for df, so that takes care of that.  One problem I'm running into, even with your suggestion is that I get bunches of 'cannot access' errors for root sub-directories, even running the command with 'sudo'.  

Any idea what's that about or how to get around those to output results for all sub-directories?

---

### Post by gmargo on 2010-03-29
It's not a great idea to run 'du' from the root directory without using the -x (--one-file-system) option.  You don't need 'du' poking about in your /proc and /sys directory.  I don't think you can harm anything, but that's probably where the error messages are coming from.  However, if you use -x, then you must run one 'du' for each main filesystem.  Personally, I have a script that essentially runs "du -x -s *" and sorts it and saves it in a local file, which is nice because it can run from any directory.

---

### Post by sitex on 2010-04-10
**du -sh**

if you want to know more basjc terminal commands listed in a-z [visit Solutionz site by clicking here]("http://solutionz.yolasite.com/linux-commands.php")

---

### Post by Lampi on 2010-04-10
```
df -Ph | awk '/%/ { printf("| %-4s | %-5s | %s\n",$5,$4,$6) }'
```
Also nice to get some sort of summary what is in use, what is unused, and where it is mounted.

---

### Post by cAlpha on 2010-04-10
> **sitex said:**
> **du -sh**

if you want to know more basjc terminal commands listed in a-z [visit Solutionz site by clicking here]("http://solutionz.yolasite.com/linux-commands.php")

Well, that's a start, but that doesn't really do what I'd needed.  Is that your site?  

> **Lampi said:**
> ```
df -Ph | awk '/%/ { printf("| %-4s | %-5s | %s\n",$5,$4,$6) }'
```
Also nice to get some sort of summary what is in use, what is unused, and where it is mounted.

What does the -P option do?  Though outside of being formatted in a cool way, it doesn't give me any more information than the 'df -h' I was starting with.  

I ended up finding a combination that suited by needs last weekend but can't remember off the top of my head what the command was.  I believe it was something like 'du / -as -max-depth--2 | sort -n'.  Using the -h (human readable) option ended up screwing with the way things were sorted--after I figured that out, it was all good.

---

