---
title: "capturing terminal output issue"
date: 2011-10-14
forum: General Help
---

### Post by maclenin on 2011-10-14
I am running a bash script, whose output I would like to "tee" to both terminal and log_file:

```
command | tee log_file
```

The command generates (let's say) 50,000 lines of output.

All 50,000 lines of output are dumped to the terminal, however, only about 15,000 lines of output make it to the log_file.

The log_file ceases to capture output after line 15,000. Lines 15,001 - 50,000 don't appear in the log_file.

Any thoughts about why the log_file comes up 35,000 lines short?

Thanks for any ideas!

---

### Post by mixmastamyk on 2011-10-14
Could some of the output be going to stderr?

---

### Post by mixmastamyk on 2011-10-14
You might try something like:

    ```
command 2>&1 | tee log_file
```

More info at:
  [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)

---

### Post by maclenin on 2011-10-15
**mixmastamyk** - thanks for the note!

Yes - I should have been more explicit - my code is, essentially...

```
command 2>&1 | tee log_file
```

...as you suggest.

Still, no joy!

---

### Post by mixmastamyk on 2011-10-16
Hmm, running out of ideas ...

What about sending it into wc -l ?  what does it give you?

---

### Post by maclenin on 2011-10-18
Hmmm, back - with a curiouser and curiouser....

I ran...

log_file.sh:
```
command.sh 2>&1 | tee log_file
```

which calls command.sh:
```
command
wc -l log_file
```

to yield **command** output and the following **wc -l** output:
```
55562 log_file
```

*55562 lines of **command** output and the single line of **wc -l** output appear in the terminal window.

*Only the first 14721 lines of **command** output appear in the log_file. The **wc -l** output does not appear in the log_file.

Hmmm.

---

### Post by gsmanners on 2011-10-18
What are you using to view log_file?

---

### Post by maclenin on 2011-10-18
mousepad / gnumeric / nano...

...and then I just opened it in AbiWord - and...joy!

It seems all the output is there. I don't understand.

Can you clarify?

Thanks, **gsmanners**, for the lead!

---

### Post by ofnuts on 2011-10-18
> **maclenin said:**
> mousepad / gnumeric / nano...

...and then I just opened it in AbiWord - and...joy!

It seems all the output is there. I don't understand.

Can you clarify?

Thanks, **gsmanners**, for the lead!Likely your utility hitting a 1MB limit...

---

### Post by maclenin on 2011-10-18
Hello, **ofnuts** - can you clarify what you mean by "utility" hitting a 1MB limit?

---

### Post by ofnuts on 2011-10-18
> **maclenin said:**
> Hello, **ofnuts** - can you clarify what you mean by "utility" hitting a 1MB limit?Some editors may decide they won't load more than 1MB of file... It used to make sense (even now, loading a 500MB log file by mistake may be a bit disrupting)

---

### Post by maclenin on 2011-10-19
> **ofnuts said:**
> Some editors may decide they won't load more than 1MB of file... It used to make sense (even now, loading a 500MB log file by mistake may be a bit disrupting)

Thanks, **ofnuts**....

I figured that was the gist - yes, agreed - seems a bit antiquated...

...also, a bit random, as I am able to view a different txt file, which has 59,000 lines of text (~2.7 MB) with the same mousepad utility (in 11.04)...but can't (fully) open the log_file in question (also a text file) - which is ~1.3 MB....

Might there be some other nuance at play?

---

