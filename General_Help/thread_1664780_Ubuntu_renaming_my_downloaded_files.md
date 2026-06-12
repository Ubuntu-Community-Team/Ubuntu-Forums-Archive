---
title: "Ubuntu renaming my downloaded files"
date: 2011-01-11
forum: General Help
---

### Post by wingnux on 2011-01-11
Whenever I download a file using Firefox or Google Chrome and it has a ' character on it's filename, the file is renamed and a \ is added before the '. It's really annoying and I'd like to know how can I solve this issue.

Thanks in advance.

Screenshot of the issue attached.

---

### Post by wingnux on 2011-01-12
Bump!

---

### Post by SPr on 2011-01-12
Having a ' in filenames is bad practice and the system is compensating for that.

Take a look at any Bash scripting tutorial to see what ' and \ mean.

---

### Post by matt_symes on 2011-01-12
Hi

It's trying to escape the **'** character that is illegal in a filename in Linux unless it is escaped.

Go to the folder where they are downloaded to and see if the **\** character is there in the filename.

Kind regards

---

### Post by SPr on 2011-01-12
Double post. Every time I submit an edit the forum software responds slowly and a new post is made.

---

### Post by SPr on 2011-01-12
Double post. Delete please.

---

### Post by SPr on 2011-01-12
It isn't illegal.
```

touch te\'st
ls te\'st

```

It's barely even bad practice but considering the question I don't think the OP has done any scripting so I kept my answer as simple as possible.

---

### Post by matt_symes on 2011-01-12
Hi

> **SPr said:**
> It isn't illegal.
```

touch te\'st
ls te\'st

```

No, it's not illegal. I was in the middle of editing my post.. when the forums went *hick* ;) (as can be seen by your three identical posts)

Try

```
touch te'st
```

though and you will see what i mean.  What is happening is to save the file name the ' character has to be escaped with a \ character.

When it saved to the hard drive te\'st becomes te'st. Check the folder where the file was downloaded to.

It's only in firefox's download dialog box that you should see the \ in front of the ' character.

Kind regards

---

### Post by wingnux on 2011-01-12
Nope, it really does save the files with the "\" character:

> wingnux@wingnux-desktop ~/Downloads $ ls Luther*
Luther Vandross - Ain\'t No Stoppin\' Us Now (1995 Remix).MP3
Luther Vandross - Ain\'t No Stoppin\' Us Now (Album Version).MP3
Luther Vandross - Ain\'t No Stoppin\' Us Now (Dead Zone).MP3
Luther Vandross - Ain\'t No Stoppin\' Us Now (Reprise).MP3

---

### Post by matt_symes on 2011-01-12
Hi

Fair enough. I stand corrected. It seems to be doing something along the lines of...

```
touch te\\\'st
```

No idea why though :confused:

I will have a play.

Kind regards

---

### Post by Slim Odds on 2011-01-12
> **wingnux said:**
> Nope, it really does save the files with the "\" character:

No.... the backslash is NOT in the filename.

Once again BASH is putting the backslash in the output.

Look at it with nautilus.

---

### Post by matt_symes on 2011-01-12
Hi

> **Slim Odds said:**
> No.... the backslash is NOT in the filename.

Once again BASH is putting the backslash in the output.

Look at it with nautilus.

He may well be right. These test files were created using touch.

```
matthew@matthew-laptop:~$ ls -l te*
-rw-r--r-- 1 matthew matthew 0 2011-01-12 18:13 te'st
-rw-r--r-- 1 matthew matthew 0 2011-01-12 18:01 te\'st
matthew@matthew-laptop:~$
``` 

Check out the attached screen shot. Quite why Firefox should be doing this though, i am not sure.

Kind regards

---

### Post by SPr on 2011-01-13
I've just tried it with IceWeasel (re-badged FireFox) from the official Debian repos and the filename is preserved.

Are the versions of Firefox exhibiting this behaviour from the Ubuntu repos or locally compiled from source?

---

### Post by Slim Odds on 2011-01-13
I think that you are continuing to confuse yourself.

BASH uses quotes (both single and double) to separate input and therefore must also deal with them differently on output.

So the ' character must be "escaped" (i.e., put a backslash in front of it). It does this on output so as to be consistent with the way it works on input and to keep pipes from breaking.

I am quite certain that Iceweasel and Firefox have no difference in the way that they handle filenames.

---

### Post by mc4man on 2011-01-13
At least here, keeping w/ this instance of a trackname w/ ' in it, bash adds a \" after the '
A \ before ' is treated as part of the filename

(though I possibly could be confused as to the issue

---

### Post by Slim Odds on 2011-01-13
"**[partial         quoting]("http://tldp.org/LDP/abs/html/varsubn.html#DBLQUO") [double quote]. ***"STRING"* preserves (from           interpretation) most of the special characters within           *STRING*. See [Chapter 5]("http://tldp.org/LDP/abs/html/quoting.html").

'**[full         quoting]("http://tldp.org/LDP/abs/html/varsubn.html#SNGLQUO") [single quote]. ***'STRING'* preserves all special           characters within *STRING*. This is a           stronger form of quoting than *"STRING"*.           See [Chapter 5]("http://tldp.org/LDP/abs/html/quoting.html").

...

\**[escape]("http://tldp.org/LDP/abs/html/escapingsection.html#ESCP") [backslash]. **A quoting mechanism for single characters.

**\X**         *escapes* the character         *X*. This has the effect of         "quoting" *X*, equivalent         to *'X'*.  The \ may         be used to quote " and ',         so they are expressed literally.
See [Chapter 5]("http://tldp.org/LDP/abs/html/quoting.html") for an in-depth explanation             of escaped characters.

...

Check out the Advanced Bash Scripting Guide. It's very helpful.
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

---

### Post by Smart Viking on 2011-01-13
```
(smartviking)-(jobs:0)-(~/tem)
(! 543)-> touch om'g
> ^C
(smartviking)-(jobs:0)-(~/tem)
(! 544)-> touch "om'g"
(smartviking)-(jobs:0)-(~/tem)
(! 545)-> echo "lol" > om'g
> ^C
(smartviking)-(jobs:0)-(~/tem)
(! 546)-> echo "lol" > "om'g"
(smartviking)-(jobs:0)-(~/tem)
(! 547)-> echo "lol" > om\'g
(smartviking)-(jobs:0)-(~/tem)
(! 549)-> cat om\'g
lol
(smartviking)-(jobs:0)-(~/tem)
(! 550)-> cat "om'g"
lol
(smartviking)-(jobs:0)-(~/tem)
(! 551)-> cat om'g
> 
> 
> ^C
```
To save peoples time.

---

### Post by SPr on 2011-01-14
> **wingnux said:**
> Nope, it really does save the files with the "\" character:
> 
wingnux@wingnux-desktop ~/Downloads $ ls Luther*
Luther Vandross - Ain\'t No Stoppin\' Us Now (1995 Remix).MP3
Luther Vandross - Ain\'t No Stoppin\' Us Now (Album Version).MP3
Luther Vandross - Ain\'t No Stoppin\' Us Now (Dead Zone).MP3
Luther Vandross - Ain\'t No Stoppin\' Us Now (Reprise).MP3



> **matt_symes said:**
> Hi

Fair enough. I stand corrected. It seems to be doing something along the lines of...

```
touch te\\\'st
```

No idea why though :confused:

I will have a play.

Kind regards

The file is being saved as 
Luther Vandross - Ain\'t No Stoppin\' Us Now (Reprise).MP3

NOT
Luther Vandross - Ain't No Stoppin' Us Now (Reprise).MP3
```

$ touch te\'st
$ ls te*
te'st

$ touch te\\\'st
$ ls te*
te'st  te\'st

```

If ' is being escaped why aren't spaces and brackets?

Luther\ Vandross\ -\ Ain\'t\ No\ Stoppin\'\ Us\ Now\ \(Reprise\).MP3

Edit:
I apologise to the OP for being condescending in one of my earlier posts.

---

### Post by mc4man on 2011-01-14
> I've just tried it with IceWeasel (re-badged FireFox) from the official Debian repos and the filename is preserved.

opera will also dl and save the file **without** the \ becoming part of the filename, with firefox and chromium the \ is now part of the name

---

### Post by SPr on 2011-01-14
> **mc4man said:**
> opera will also dl and save the file **without** the \ becoming part of the filename, with firefox and chromium the \ is now part of the name

Exactly. Where did you get Firefox from? Are there any extensions/add ons installed that could be interfering?

---

### Post by wingnux on 2011-01-14
I'm using firefox from ubuntu's repo, gonna try disabling all extensions and downloading a test file.

---

### Post by wingnux on 2011-01-14
I'm using firefox from ubuntu's repo, gonna try disabling all extensions and downloading a test file.

---

### Post by wingnux on 2011-01-14
I've installed both Google Chrome and Mozilla Firefox from Ubuntu's stable repository.
Just disabled all installed add-ons and tried to download the file again, it still renames it.

---

### Post by wingnux on 2011-01-14
Sorry for triple posting!

---

### Post by SPr on 2011-01-15
In that case it's a bug in Firefox and needs reporting.

---

