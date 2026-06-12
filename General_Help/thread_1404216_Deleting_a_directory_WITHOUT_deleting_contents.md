---
title: "Deleting a directory WITHOUT deleting contents?"
date: 2010-02-11
forum: General Help
---

### Post by miggerish on 2010-02-11
I know that rm -r [directoryname] will delete the specified directory and all contents, but how can I delete a directory WITHOUT deleting its contents?

Like it should delete the directory, and everything that was in the directory will just move up to the next directory.

Example:

i have /opt/lampp/rir/div

i want to delete lampp so that rir moves up in the place of lampp and everything in it moves up.

so after deletion of the directory, it will look like this:

/opt/rir/div

---

### Post by mechro on 2010-02-11
I'm not a command line expert so please, please run a test before you do this...

mv -r /opt/lampp/rir/div /opt/rir/div

Suggest you also read the manpage for *mv*

---

### Post by miggerish on 2010-02-11
> **mechro said:**
> I'm not a command line expert so please, please run a test before you do this...

mv -r /opt/lampp/rir/div /opt/rir/div

Suggest you also read the manpage for *mv*

-r is not a valid option in mv

Someone PLease help me!

---

### Post by wojox on 2010-02-11
So leave out the -r.

---

### Post by mechro on 2010-02-11
oops! How embarrassing! I thought I'd googled a manpage... Sorry.

As wojox says, mv without the -r is worth a try.

---

### Post by Mark Phelps on 2010-02-11
> **miggerish said:**
> I know that rm -r [directoryname] will delete the specified directory and all contents, but how can I delete a directory WITHOUT deleting its contents?

What folks are not telling you directly is that this is simply not possible!

What they are telling you to do is the following:
1) move the files contained in the directory to a different directory
2) remove the now empty directory

---

### Post by Ordes on 2010-02-11
yup, not possible...

1) move content
2) delete folder

...and i dont know any OS where this is actually possible. You always have to first move the content out, if you dont want it to get deleted...

---

### Post by weblordpepe on 2010-02-11
Never say impossible with linux :P

OK this is a pretty rough command line. Essentially you'll want to CD to the directory, move everything to .., switch back to .. and delete the subdir.

For example, lets say you are in **/home/joe/** and there's a crap load of files in **/home/joe/blow/** that you want moved into the parent directory, **/home/joe**:

```
cd ./blow && mv -t .. * && cd .. && rm -rf ./blow
```
I have used **&&** to put it all on the same line, but broken down you have.


Cd to ./blow:
```
cd ./blow
```

Move everything to parent dir:
```
mv -t .. *
```

Cd back to parent dir:
```
cd ..
```

Remove ./blow:
```
rm -rf ./blow
```

And there you have it. Removed directory and all files moved to the parent dir. And on one line, thanks to the **&&** thingiedoodle.

---

### Post by falconindy on 2010-02-11
Squeezing out some keystrokes...

```
mv /opt/{lampp/,}rir/div && rm -r !:1
```

---

### Post by mechro on 2010-02-11
> **Ordes said:**
> yup, not possible...

1) move content
2) delete folder



I agree... so move/copy rir/div to opt/ and delete lampp/ ...

cp -r /opt/lampp/rir /opt

rm -r /opt/lampp



Edit... err... I bow to the elegance above!

---

### Post by weblordpepe on 2010-02-11
> **falconindy said:**
> Squeezing out some keystrokes...

```
mv /opt/{lampp/,}rir/div && rm -r !:1
```I think I just got served :P

---

### Post by Mark Phelps on 2010-02-11
> **weblordpepe said:**
> Never say impossible with linux :P

Actually, you confirmed my original statement -- because the code you provided does EXACTLY what I stated -- moves the files, then deletes the empty directory.

But ... to be fair ... he asked without "deleting contents", not without "moving files".

So, you're still correct. :)

---

### Post by BentFX on 2010-02-11
Sometimes elegance is in simplicity... Simplicity is certainly best at the lower end of the learning curve...

```
mv foldername/* .;rm -r foldername
```

That's how I would do it anyway.

---

### Post by falconindy on 2010-02-11
> **BentFX said:**
> Sometimes elegance is in simplicity... Simplicity is certainly best at the lower end of the learning curve...

```
mv foldername/* .;rm -r foldername
```

That's how I would do it anyway.
You forgot the 'cd' at the start. There's nothing insanely magical about my method. It uses brace expansion (a Bash feature), and history access (available from any shell). It may look somewhat cryptic, but it's Shell Survival 101.

---

### Post by weblordpepe on 2010-02-13
[IMG]http://www.mattcutts.com/images/duty_calls.png[/IMG]
My friends we have stumbled into the vally of the ever-shrinking shell code :P

I hereby launch a challenge for this to be even shorter.

---

### Post by jwbrase on 2010-02-13
You can always write your own utility (or option to an existing utility) to do whatever you want to do...

---

