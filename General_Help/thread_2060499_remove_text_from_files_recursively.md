---
title: "remove text from files recursively?"
date: 2012-09-20
forum: General Help
---

### Post by sohlinux on 2012-09-20
I have a lot files inside the home folder and its sub folders and I need to remove all the text from them. I can do them individually with a command like the following but I want to remove all the text from all the files called error.txt from all folders and sub folders in /home recursively.

tail -5 /home/error.txt > /home/error.txt

thanks

---

### Post by Lars Noodén on 2012-09-20
[find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html) ought to do the trick.  You'll have to use a temporary file to carry the changes because the first thing the redirect does is to overwrite the destination file.

```

[s]find /some/path/ -name 'error.txt' -exec sh -c "tail -n 5 {} > /tmp/foo; mv /tmp/foo {};" \;[/s]

```

Edit: See [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by steeldriver on 2012-09-20
is there any particular reason you want to use 'tail'? you could use the [ _[COLOR=Blue]sed one-liner[/COLOR]_ ]("http://sed.sourceforge.net/sed1line.txt") version of 'tail'

```
# print the last 10 lines of a file (emulates "tail")  
sed -e :a -e '$q;N;11,$D;ba'
```interactively to avoid the temp file (changing the '11' to '6' to make it tail -5)

```
 find /some/path/ -name 'error.txt' -exec sed -i -e :a -e '$q;N;6,$D;ba' "{}" \;
```

You can remove the -i to do it NON-interacively (won't actually write the changes) just to see what happens

---

### Post by Lars Noodén on 2012-09-20
@steeldriver, that's a much more elegant solution.  Do you have any recommendations for good learning resources on sed?

---

### Post by steeldriver on 2012-09-20
TBH everytime I try to do anything in 'sed' I find myself having to learn it all over again! it's not the easiest tool (especially once you get into the multi-line stuff like this)

The Krumins 'one-liners explained' web resource is pretty thorough - although I often find myself still confused by the explanations

[http://www.catonmat.net/blog/sed-one-liners-explained-part-one/](http://www.catonmat.net/blog/sed-one-liners-explained-part-one/)

I'm not even sure if 'sed' is the smartest choice here - there may be a simpler truncate tool that I don't know about

[The particular sed expression above basically works by maintaining a rolling buffer of 5 lines by appending (N) to the bottom and deleting (D) from the top of the pattern space, then quitting and printing the pattern space (q) when it hits the last line ($)]

---

### Post by sohlinux on 2012-09-20
thanks guys, they both did the trick :D

---

