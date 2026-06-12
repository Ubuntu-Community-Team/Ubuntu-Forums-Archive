---
title: "backslash in sed"
date: 2011-12-04
forum: General Help
---

### Post by driebel on 2011-12-04
I am trying to edit some numbers in scientific notation to be used in a LaTeX document.  The numbers them selves are printed out:

1.23E-4

And I would like this to be pretty in my pdf, so I would like that number to appear as

1.23 \times 10^{-4}

I've got everything working except the \ in front of the times.  How do I get sed to actually put that in place?  I've tried:

sed s:E:\times 10^{: old >new
sed s:E:/\times 10^{: old >new
sed s:E:\/times 10^{: old>new
sed s:E:"\times 10^{": old>new

and other combinations of quotes and slashes I won't bore you with.  Somehow, I always end up with the t being removed from times and 4-5 spaces inserted instead of just \t.

Anyone know the answer?

Thanks,
Dave

---

### Post by driebel on 2011-12-04
SOLVED:  Not exactly sure why, but the magic combo here is single quotes around the whole command and a double backslash

sed 's:E:\\times 10^{:' old >new

---

### Post by DaithiF on 2011-12-07
Hi,
I would suggest you always put qotes around your sed expressions unless they are trivially simple, otherwise you risk the shell's processing of your line interfering with what you want to pass to sed.

in your example:
```
sed s:E:\times 10^{: old 
```

this will result in sed error (unterminated 's' command) because bash will split the arguments to sed by whitespace and therefore pass 3 arguments: 
1.  s:E:\times
2.  10^{:
3. old
and so sed barfs on the 'unterminated command' contained in 1.

Quoting with '' results in the correct arguments getting passed to sed.  Equivalently you could escape the space character and leave off the quotes, but thats kinda silly unless your keyboards ' key is missing or you have a real dislike of it.
```
sed s:E:\times\ 10^{: old

```

The second problem with not quoting is that \t gets interpreted by the shell as an escape sequence but not a very meaningful one ... \t gets expanded to just t.
So by the time sed gets its arguments they look like:
1.  s:E:times 10^{
2.  old
so in your result you don't get the slash you expect.

again if you hated quotes :) you could prevent this by escaping the '\' character with another '\', ie.:
sed s:E:\\times\ 10^{: old
Now sed gets the arguments:
1.  s:E:\times 10^{
2.  old
but unfortunately you get the result:
```
1.23    imes 10^{

```because \t is special to sed and means a tab character.

but if you really really don't like quotes you could prevent this with another set of escapes:
```
sed s:E:\\\\times\ 10^{: old

```
the shell will replace the \\ with a single \ and the following \\t with \t, so that sed gets the arguments:
1.  s:E:\\times 10^{
2.  old
and now sed treats the \\t not as a tab character but as a literal \t, so you get the result you want.

but to cut a long story short :), just use quotes, and remember that \t to sed means a tab char, whereas \\t means the literal sequence \t

---

### Post by sisco311 on 2011-12-07
@DaithiF

+1

> **driebel said:**
> SOLVED:  Not exactly sure why, but the magic combo here is single quotes around the whole command and a double backslash

sed 's:E:\\times 10^{:' old >new

The single quotes are interpreted by the shell (most likely bash)

and the backslashes are interpreted by the command (sed).

See:
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://wiki.bash-hackers.org/syntax/words](http://wiki.bash-hackers.org/syntax/words)

---

