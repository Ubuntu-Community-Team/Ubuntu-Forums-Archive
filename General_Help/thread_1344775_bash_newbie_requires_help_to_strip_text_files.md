---
title: "bash newbie requires help to strip text files"
date: 2009-12-03
forum: General Help
---

### Post by marbour on 2009-12-03
Hello all.

Thanks for making this community comes true.

I am new at bash and require help sorting a log file of my creation.

Out of ±1277 lines, I need to remove all those containing an exact string of text to be left with the only 2-3 lines that interest me.

How should I go about this problem and could someone direct me towards reading so that I can learn about what to do.

For example: in file /home/user/scanresults.txt, I want to remove lines containing "ImageMagik" and keep only the others.

Any pointer will be very much appreciated.

Regards

Marc

---

### Post by marbour on 2009-12-03
Sorry... the log files are created with this command so maybe it's not obligated to create a script to sort it out
```
grep -iR 'HTTP_SHELL' *.* > /home/user/scanresult.txt
```

Thanks.

---

### Post by jegerjensen on 2009-12-03
the grep command is your friend.

```

cat logfile.txt | grep search_pattern

```

In your case you want to invert the matches, so you apply the -v option

```

cat logfile.txt | grep -v ImageMagik

```

man grep gives you all the glory details...

---

### Post by jegerjensen on 2009-12-03
> **marbour said:**
> Sorry... the log files are created with this command so maybe it's not obligated to create a script to sort it out
```
grep -iR 'HTTP_SHELL' *.* > /home/user/scanresult.txt
```

Thanks.

Oh, in that case you should be able to filter it before sending it to file:

```
grep -iR 'HTTP_SHELL' *.* | grep -v ImageMagick > /home/user/scanresult.txt
```

---

### Post by marbour on 2009-12-03
Wow... that simple?

Am I correct assuming I could get the result into a txt file as such```
cat logfile.txt | grep -v ImageMagik > scanresults2.txt
```
?

Marc

---

### Post by marbour on 2009-12-03
man... You're faster then me!

Wow.

I'll man this right away. 

I almost feel stupid not having thaught of this myself.

Thanks a million.

Marc.

---

### Post by jegerjensen on 2009-12-03
> **marbour said:**
> Wow... that simple?

Am I correct assuming I could get the result into a txt file as such```
cat logfile.txt | grep -v ImageMagik > scanresults2.txt
```
?

Marc

That should work as you expect.  Glad to be able to help ;)

---

