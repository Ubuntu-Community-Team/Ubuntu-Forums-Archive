---
title: "Sed not recognising &quot;$&quot; regular expression in Hardy"
date: 2009-10-08
forum: General Help
---

### Post by Irihapeti on 2009-10-08
I've discovered that I can't consistently get sed to recognise the $ regex for the end of a line in Ubuntu Hardy.

If I run the command ```
sed 's/foobar$/foo/p' myfile.txt
``` (where myfile.txt contains lines ending in "foobar") it does what it's supposed to. But if I do something fancier, such as trying to strip trailing slashes ```
sed 's|/$||p'
``` it does nothing. I tried running sed from a Hardy liveCD, in case I'd messed up a config file or something, and still the same (non)result.

I've just realised that this error is causing a program not to install properly - the install script uses a similar routine and sed in Hardy isn't running it. The relevant output is ```
for i in ca.mo cs.mo de.mo el.mo es.mo fi.mo fr.mo hu.mo it.mo ja.mo lt.mo nl.mo pl.mo pt.mo ru.mo sv.mo tr.mo uk.mo zh_CN.mo; do \
		lang=`echo $i | sed 's/\.mo$//'`; \
		/bin/bash /home/ja/src/osmo-svn-1/install-sh -d /usr/share/locale/$lang/LC_MESSAGES; \
		/usr/bin/install -c -m 644 $i /usr/share/locale/$lang/LC_MESSAGES/osmo.mo; \
	done

```
I get the error messages:```
/usr/bin/install: cannot stat `ca.mo': No such file or directory
/usr/bin/install: cannot stat `cs.mo': No such file or directory
/usr/bin/install: cannot stat `de.mo': No such file or directory
/usr/bin/install: cannot stat `el.mo': No such file or directory
....

```

Is there some setting or other that I need to change? Or another version of sed that I could install?

---

### Post by niteshifter on 2009-10-08
Hi,

Not a sed problem.

The for loop iterates over the list of files (ca.mo cs.mo de.mo ...) and sets each file name in the varible i.

On down /usr/bin/install is invoked as:
```
/usr/bin/install -c -m 644 $i /usr/share/....
```

install is basically a copy command:
```
install [OPTIONS] SRC  DEST
```

Here, SRC is $i - the variable set at the head of the loop. The errors are telling that the files ca.mo cs.mo de.mo ... are not present in the script's current working directory.

This:
```
sed 's|/$||p'
```
as given, will do nothing. There's nothing there for sed to work on.

This works:
```
echo 'trailing/' | sed 's|/$||'
```

---

### Post by Irihapeti on 2009-10-08
Sorry, my second example should have read:

```
sed 's|/$||p' inputfile.txt
```
where inputfile.txt has several thousand lines ending in /

If I run ```
sed 's|/|;|p' inputfile.txt
```
(same file), every / is turned into ; as expected.

The install example wasn't written by me, and appears to have worked for others who have compiled the program (Osmo).

---

### Post by dcstar on 2009-10-09
> **Irihapeti said:**
> Sorry, my second example should have read:

```
sed 's|/$||p' inputfile.txt
```
where inputfile.txt has several thousand lines ending in /
.........
How about:

```
sed 's|\/$||p'
```

---

### Post by Irihapeti on 2009-10-09
> **dcstar said:**
> How about:

```
sed 's|\/$||p'
```

Sorry, still doing nothing.

Just wondering, would it have anything to do with the fact that the file has Chinese characters in it? None of them are right before the final slash, though.

Edit: and I don't think there would be any Chinese characters in the Osmo installation script.

---

### Post by niteshifter on 2009-10-09
Hi,

I doubt Chinese characters are the problem. Two things come to mind:

Your file was generated on a Windows machine. They end lines with CR-LF, sed 's|/$||' will fail here, the / isn't the last character before EOL, CR is. 

The lines ends with a whitespace character like space or tab.

Try looking at the problem file with a hex editor, see what's really just before EOL.

Below is a simple test of sed's behavior on my box (Hardy 8.04.3):
```
dlk@dlk-lt-1420:~/test$ cat testfile.txt
line one/
line two/
line three/

dlk@dlk-lt-1420:~/test$ sed 's|/$||' testfile.txt
line one
line two
line three

dlk@dlk-lt-1420:~/test$ sed --version
GNU sed version 4.1.5
Copyright (C) 2003 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE,
to the extent permitted by law.
dlk@dlk-lt-1420:~/test$ 

```

---

### Post by Irihapeti on 2009-10-09
> **niteshifter said:**
> Your file was generated on a Windows machine. They end lines with CR-LF, sed 's|/$||' will fail here, the / isn't the last character before EOL, CR is. 
...
Try looking at the problem file with a hex editor, see what's really just before EOL.

I think that might be the problem - I see repeated occurrences of 0A0D in the hex panel of Ghex. The file was one I downloaded, so it could well have been set up on a Windows machine.

What are my options here, then? Some further sed trickery, or is another app needed?

---

### Post by Lars Noodén on 2009-10-09
```
sed 's/\x0D$//;s/foobar$/foo/p' myfile.txt'
```

---

### Post by Irihapeti on 2009-10-09
I discovered one answer to my question shortly after my last post, only I was too tired to post back straight away :)

```
sed 's|/\r$||p' inputfile.txt
```

And Lars' suggestion also does the job.

Thanks, guys. I hadn't thought of the dreaded CRLF being the culprit, and was slowly going mad (well, madder than usual :)) in the process.

I can mark this one solved.

Now to work out what to do about the install script. Maybe I need to file a bug report...

---

