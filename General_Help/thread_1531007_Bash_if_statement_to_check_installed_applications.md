---
title: "Bash if statement to check installed applications"
date: 2010-07-14
forum: General Help
---

### Post by iMetaphysikz on 2010-07-14
Hi I know with if statements in bash you can do

```
if [ $fruit = apple ]
        then echo "Good, I like Apples"
      fi

```

but I was wondering if you could do something like this:

```
if [apt-cache pkgnames smbfs = smbfs doesn't exist]
          the apt-get install smbfs
      fi

```

If so how would you capture the output from apt-cache pkgname smbfs to determine if it's installed?

---

### Post by Zorgoth on 2010-07-14
If zombie is your variable name,
zombie=`apt-cache pkgnames smbfs`
Then you can parse zombie with a for loop

---

### Post by iMetaphysikz on 2010-07-14
> **Zorgoth said:**
> If zombie is your variable name,
zombie=`apt-cache pkgnames smbfs`
Then you can parse zombie with a for loop

I think I understand what you mean do the command apt-cache pkgnames smbfs in a for loop and the collect the output into a variable which can then be used with the if statement to match against smbfs?

---

### Post by mikewhatever on 2010-07-14
Something like this should work:
```
test=$(apt-cache pkgnames smbfs); echo $test
```

However, the problem here is that 'apt-cache pkgnames smbfs' doesn't show if smbfs is installed or not.:p

---

### Post by Vaphell on 2010-07-14
can't you simply run apt-get install without testing? you won't break it after all. If it's installed already - nothing happens, if not - you install it.

---

### Post by nmaster on 2010-07-14
to list all installed packages, try this:
```

dpkg &#8211;get-selections | grep -v deinstall 

```

you can direct this into a file if you want or just pipe into grep to find the package you're looking for

---

### Post by iMetaphysikz on 2010-07-14
> **mikewhatever said:**
> Something like this should work:
```
test=$(apt-cache pkgnames smbfs); echo $test
```

However, the problem here is that 'apt-cache pkgnames smbfs' doesn't show if smbfs is installed or not.:p

Any idea's on how to find out if smbfs is installed?
All i'm doing is checking if it's installed and if not apt-get install smbfs to install. :)

---

### Post by iMetaphysikz on 2010-07-14
> **Vaphell said:**
> can't you simply run apt-get install without testing? you won't break it after all. If it's installed already - nothing happens, if not - you install it.

I could, is there a way to remove output if the application is installed?

---

### Post by Vaphell on 2010-07-14
[http://www.cyberciti.biz/faq/how-to-redirect-output-and-errors-to-devnull/](http://www.cyberciti.biz/faq/how-to-redirect-output-and-errors-to-devnull/)

---

### Post by iMetaphysikz on 2010-07-14
> **Vaphell said:**
> [http://www.cyberciti.biz/faq/how-to-redirect-output-and-errors-to-devnull/](http://www.cyberciti.biz/faq/how-to-redirect-output-and-errors-to-devnull/)

Thanks that's done the trick :)

---

### Post by sisco311 on 2010-07-14
> **iMetaphysikz said:**
> Any idea's on how to find out if smbfs is installed?
All i'm doing is checking if it's installed and if not apt-get install smbfs to install. :)

Something like:
```
dpkg-query -W -f='${Status}' smbfs &> /dev/null || sudo apt-get install smbfs
```
should do the trick

---

