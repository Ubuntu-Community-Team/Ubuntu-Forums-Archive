---
title: "Please help me with this BASH script"
date: 2011-12-02
forum: General Help
---

### Post by cha0s619 on 2011-12-02
I have a directory called Books. Within this directory there are a number of pdf ebooks I downloaded and the books are within their own directories. I want to write a script that goes into each directory and copies the pdf from its current dir to the main Books dir. The code I have now is not working. How can I edit it to make it perform this task. Any additional info on what's going on will be greatly appreciated. Thanks


```


for i in `find -type d`
do
    cd $i
    cp *.pdf /home/ubuntu/Books/
    cd ..
done


```

---

### Post by MG&amp;TL on 2011-12-02
What's 'not working' about it?

Replace '/home/ubuntu/Books' with either '/home/$USER/Books' or '../'. For a start.

---

### Post by Lars Noodén on 2011-12-02
Why not use just [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1.html) by itself?

```

find /path/to/dir -name '*.pdf' -exec cp "{}" /home/ubuntu/Books/ \;

```

---

### Post by pengyou on 2011-12-02
> [FONT=monospace][/FONT]What's 'not working' about it?

Replace '/home/ubuntu/Books' with either '/home/$USER/Books' or '../'. For a start. 	 

Wouldn't that be
```

~/ubuntu/books

```
?

Also your

```
cd ..
```

Is inadequate.
I used the find command that you did and received dirs 3 levels deep at least.

---

### Post by pengyou on 2011-12-02
> **Lars Noodén said:**
> Why not use just [find]("http://manpages.ubuntu.com/manpages/precise/en/man1/find.1.html") by itself?

```

find /path/to/dir -name '*.pdf' -exec cp "{}" /home/ubuntu/Books/ \;

```

:o
Please explain?
ORZ
i could rtfm but that's a pretty complex line.

---

### Post by Lars Noodén on 2011-12-02
I think I see how your script can be broken.  [font=Courier New]find[/font] can find directories more than one level deep and [font=Courier New]cd ..[/font] only goes back up a single level.  You can use [font=Courier New]pushd[/font] and [font=Courier New]popd[/font] which are built into [bash](http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html).

```

for i in `find -type d`
do
    pushd .
    cd $i
    cp *.pdf /home/ubuntu/Books/
    popd
done

```

I'd still recommend using only find as described above in [#3](http://ubuntuforums.org/showpost.php?p=11507222&postcount=3)

---

### Post by nothingspecial on 2011-12-02
See Bash Pitfalls numbers one and two

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by cha0s619 on 2011-12-02
> **MG&TL said:**
> What's 'not working' about it?

Replace '/home/ubuntu/Books' with either '/home/$USER/Books' or '../'. For a start.

The path is fine. The problem is that `find -type d` isn't creating a proper directory path that BASH can cd into. For example here is the output when I'm in the Books directory:


```


ubuntu@ubuntu-desktop:~/Books$ find -type d
.
./The Busy Coder's Guide to Advanced Android Development - (Malestrom)
./Beginning iPhone Development - Exploring the iPhone SDK
./Head First Java 2nd edition - Orginal PDF non-scanned by ab4cd
./Data Abstraction & Problem Solving with Java
./Learning to Program with Python-2nd Ed. Torrent
./Learning to Program with Python-2nd Ed. Torrent/Python Programming Source code files copy
./Java The Complete Reference - 7th Edition [DwzRG]
./Beginning.Programming.With.Java.For.Dummies.2nd.Edition
./Python for Unix and Linux System Administration
./Sams Teach Yourself Android Application Development 24 Hours
./For.Dummies.Java.For.Dummies.5th.Edition.Aug.2011
./Beginning Android Application Development - (Malestrom)
ubuntu@ubuntu-desktop:~/Books$ 



```

The spaces are not escaped, so in the first instance, it looks for a directory called /The instead of "./The Busy Coder's Guide to Advanced Android Development - (Malestrom)"

---

### Post by nothingspecial on 2011-12-02
I should also mention that backticks are depreciated


```
for i in `commands`
```

should now be

```
for i in $(commands)
```

---

### Post by nothingspecial on 2011-12-02
> **cha0s619 said:**
> The path is fine. The problem is that `find -type d` isn't creating a proper directory path that BASH can cd into. For example here is the output when I'm in the Books directory:


```


ubuntu@ubuntu-desktop:~/Books$ find -type d
.
./The Busy Coder's Guide to Advanced Android Development - (Malestrom)
./Beginning iPhone Development - Exploring the iPhone SDK
./Head First Java 2nd edition - Orginal PDF non-scanned by ab4cd
./Data Abstraction & Problem Solving with Java
./Learning to Program with Python-2nd Ed. Torrent
./Learning to Program with Python-2nd Ed. Torrent/Python Programming Source code files copy
./Java The Complete Reference - 7th Edition [DwzRG]
./Beginning.Programming.With.Java.For.Dummies.2nd.Edition
./Python for Unix and Linux System Administration
./Sams Teach Yourself Android Application Development 24 Hours
./For.Dummies.Java.For.Dummies.5th.Edition.Aug.2011
./Beginning Android Application Development - (Malestrom)
ubuntu@ubuntu-desktop:~/Books$ 



```

The spaces are not escaped, so in the first instance, it looks for a directory called /The instead of "./The Busy Coder's Guide to Advanced Android Development - (Malestrom)"

Look at the bash pitfalls I linked. This is where you are going wrong :)

---

### Post by CharlesA on 2011-12-02
> **nothingspecial said:**
> Look at the bash pitfalls I linked. This is where you are going wrong :)

Yep. It's easier to just use find with the -exec switch.

---

### Post by nothingspecial on 2011-12-02
If the directories are only one deep then something like

```
for i in *; do if [[ -d "$i" ]]; then cp "$i"/*.pdf /home/ubuntu/books; fi; done
```

should do it. It's not very elegant and will have errors though.

---

### Post by cha0s619 on 2011-12-02
> **nothingspecial said:**
> See Bash Pitfalls numbers one and two

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)


Thanks! Thats gonna save me lots of head scratching.

---

### Post by Slim Odds on 2011-12-02
> **Lars Noodén said:**
> I think I see how your script can be broken.  [FONT=Courier New]find[/FONT] can find directories more than one level deep and [FONT=Courier New]cd ..[/FONT] only goes back up a single level.  You can use [FONT=Courier New]pushd[/FONT] and [FONT=Courier New]popd[/FONT] which are built into [bash]("http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html").

```

for i in `find -type d`
do
    pushd[COLOR=Red] $i[/COLOR]
    #cd $i
    cp *.pdf /home/ubuntu/Books/
    popd
done

```I'd still recommend using only find as described above in [#3]("http://ubuntuforums.org/showpost.php?p=11507222&postcount=3")

pushd takes an argument which is the directory to switch to

---

### Post by Lars Noodén on 2011-12-02
> **pengyou said:**
> :o
Please explain?
ORZ
i could rtfm but that's a pretty complex line.

```

find /path/to/dir -name '*.pdf' -exec cp "{}" /home/ubuntu/Books/ \;

```

find - self evident ;)
/path/to/dir - some directory to start the find in
name - find anything ending with .pdf
exec - pass to the system the following
cp - copy
{} - the result of find
\; the end of the exec

Please do look at the manual for all the details.

---

### Post by Slim Odds on 2011-12-02
> **Lars Noodén said:**
> ```

find /path/to/dir -name '*.pdf' -exec cp "{}" /home/ubuntu/Books/ \;

```find - self evident ;)
/path/to/dir - some directory to start the find in
name - find anything ending with .pdf
exec - pass to the system the following
cp - copy
{} - the result of find
\; the end of the exec

Please do look at the manual for all the details.

find with -exec is very powerful, but it does take some learning.

But, depending on what program you are going to "-exec", sometimes it's much better to use the output of find in a for loop.

---

### Post by Lars Noodén on 2011-12-03
> **Slim Odds said:**
> But, depending on what program you are going to "-exec", sometimes it's much better to use the output of find in a for loop.

That the way I'm trying to unlearn.  It does not work if there are [spaces in the filename](http://mywiki.wooledge.org/BashPitfalls)

---

