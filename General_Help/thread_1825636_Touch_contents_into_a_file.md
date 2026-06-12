---
title: "Touch contents into a file"
date: 2011-08-15
forum: General Help
---

### Post by ehime on 2011-08-15
I know that I can do something along the lines of

```

touch /var/www/index.html | echo "echo some contents" >> /var/www/index.html

```

but would like to do this without having to specify the directory again with echo, and maybe even use linebreaks / tabs on the echo in. Anyone know a neat one liner?

---

### Post by Bachstelze on 2011-08-15
You are very confused.

First, touch is not needed, writing to the file will touch it anyway. Second, what is this pipe doing here? Sure, it technically works, but a ; or && would be more in order. Last, >> will append to the file. Again, it works, but I believe you mean > instead.

---

### Post by mendhak on 2011-08-15
Not a one liner, but what about

cat /var/www/index.html

Then the prompt should go to the next 'line', which will be empty, where you can type away.  When you're done, press Ctrl+D and it should take all of that input and put it into the index.html.

---

### Post by Bachstelze on 2011-08-15
> **mendhak said:**
> Not a one liner, but what about

cat /var/www/index.html


Nope. This command will output the contents of the file and return to the shell. What you meant was

```
cat > /var/www/index.html
```

---

### Post by AlphaLexman on 2011-08-15
> **ehime said:**
> maybe even use linebreaks / tabs on the echo
Here is an example to use line breaks [COLOR=Red]\n[/COLOR] and tabs [COLOR=Red]\t[/COLOR] with the echo command...
```
echo [COLOR=Red]-e[/COLOR] "This is the first line[COLOR=Red]\n[/COLOR]This is the second line[COLOR=Red]\n\t[/COLOR]This is the third line tabbed" > ehime.txt
```
Also don't forget the [COLOR=Red]-e[/COLOR] option!

---

### Post by ehime on 2011-08-15
Thanks Alpha, just what I was thinking

---

### Post by nothingspecial on 2011-08-15
You can invoke your editor from the prompt by pressing Ctrl-X then Ctrl-E (nano by default)

a stupid example........

Ctrl-X, Ctrl-E

```
echo '
blah
blag
	blah' > blah.txt
```

save and close

then try ```
cat blah.txt
```
 
Would help if I could tell what you are trying to achieve.

---

