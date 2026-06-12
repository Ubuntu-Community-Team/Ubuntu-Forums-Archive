---
title: "Pipe terminal output to kate"
date: 2012-03-01
forum: General Help
---

### Post by bbrg548 on 2012-03-01
This may be a simple question, but I've searched here and on Google and can't find an answer. I'm trying to pipe text output from gpg to the kate text editor in Kubuntu. I've been using a script running the following command to do it in gedit:

```
gpg -d ~/Documents/Business/filename.txt | gedit
```

("filename.txt" is a text file with ascii armored content) That works in gedit - the decrypted text is piped to the editor and I can reference it and then close without actually creating a new file with the decrypted text, which helps keep it secure.

The problem is, the same command with "kate" substituted for gedit ```
gpg -d ~/Documents/Business/Logins.txt | kate
```just opens up an empty kate window. I also get the following in the terminal, after the gpg output:
```
Object::connect: No such slot KateExternalToolsPlugin::viewDestroyed(QObject*)
```

I would prefer to use kate for this, partly for esthetic reasons (it doesn't match my theme, and looks plain ugly), partly because I'm starting to like kate more than gedit as a plaintext/code editor, but also because doing this with gedit in KDE always opens with an extra "untitled" tab.

Any ideas?

---

### Post by papibe on 2012-03-01
I'm afraid that won't work. At least that way. Both gedit and kate are GUI program not designed to be used on a pipe like that.

These are a few ideas:

You can browse the results using 'less' (similar to 'more'):
```
gpg -d ~/Documents/Business/filename.txt  |  less
```
or you can create a file with the output and immediately open it with the editor:
```
gpg -d ~/Documents/Business/filename.txt > otherfile.txt; gedit otherfile.txt
```
Hope it helps.
Regards.

---

### Post by cortman on 2012-03-01
Until I read that you are not using gedit for aesthetic reasons, I was about to suggest just piping it to

```
cat
```

and reading it in the terminal...

---

### Post by Khayyam on 2012-03-01
Actually this is a limitation of the *nix OS, having provided the facility for redirection there has been no facility provided for programs that, for whatever reason, are constructed with some other operating system in mind.

-1 Linux

Sarcasm provide by the CLI Liberation Front ... >CLILF< ... all directions all ways.

best ... khay

---

### Post by bbrg548 on 2012-03-02
> **papibe said:**
> I'm afraid that won't work. At least that way. Both gedit and kate are GUI program not designed to be used on a pipe like that.
Which is odd, becuase it *does* work with gedit.

> **papibe said:**
> These are a few ideas:

You can browse the results using 'less' (similar to 'more'):
```
gpg -d ~/Documents/Business/filename.txt  |  less
```
Unfortunately, I also need to be able to edit the file, at least occasionally.
> **papibe said:**
> 
or you can create a file with the output and immediately open it with the editor:
```
gpg -d ~/Documents/Business/filename.txt > otherfile.txt; gedit otherfile.txt
```

As I said, I don't want to create a file of the decrypted text and then have to delete it every time to maintain security, so that won't work either.

Really, I only started using the terminal and piping it to gedit because they took the gpg plugin away, and haven't bothered to replace it.  ](*,)

A better solution would be a gpg plugin or script for kate, but I haven't had any luck finding anything like that, either, and I don't have the knowledge to do it myself, or the free time to learn how.

---

### Post by bbrg548 on 2012-03-07
Well, I wouldn't call it solved, but I've found a workaround. KGpg has a built in text editor. Opening the file from the GUI is a bit clumsy because I have to run KGpg and open the editor from that, then open the file from the editor, but it works.

The other way is to open it from the command line using ```
kgpg -s <path_and_filename>
```
(the -s option tells it to open the file in the editor). The odd thing is that while this command will open the file directly in the Kgpg editor, running the exact same command from a shell script opens a blank file.

---

### Post by papibe on 2012-03-07
:o Very interesting. Thanks for sharing that!

Kind Regards.

---

### Post by bbrg548 on 2012-03-08
And just to update my previous comment, it turns out that I was overlooking the obvious. Running ```
kgpg -s <path_and_filename>
``` from a script requires using the *full* path rather than a relative path, even if the script is in the same directory as the target file. Do that and it works just fine.

Duh. #-o

---

### Post by mersey01 on 2012-04-29
Running kate --help revealed a likely candidate and it works for me

cat <file> | kate -i

---

