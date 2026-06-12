---
title: "Emacs -- Run Shell Command w/o Output"
date: 2011-07-12
forum: General Help
---

### Post by sgy on 2011-07-12
I write LaTeX in Emacs and then run a shell script to process the LaTeX code.  I used to run a subshell buffer with M-x shell and then execute the script from within there, but this results in a lot of switching between buffers, which seems unnecessary.  Then, I found out about executing shell commands with M-! cmd RET, as described here:

[http://www.nongnu.org/emacsdoc-fr/manuel/shell.html](http://www.nongnu.org/emacsdoc-fr/manuel/shell.html)

The problem with this is that the output from the script splits my screen.  It's a nuisance, and I would like to run the script without any output.  I've tried appending > /dev/null to the command, but it doesn't work.

For example, when from within Emacs I enter M-! followed by ```
sh make.sh > /dev/null
``` it splits my screen so that one portion displays output from the make.sh script.  I want it to run silently, and leave my Emacs buffers alone.

Any thoughts would be appreciated.

Thanks.

---

### Post by enimeizoo on 2011-07-12
What you tried with make works with ls. So I think you should redirect stderr too.

make > /dev/null 2> /dev/null

It works here.

(edit) I didn't know about the &>, very useful, thanks!

---

### Post by lykwydchykyn on 2011-07-12
The > only redirects STDOUT, any errors or warnings (or anything directed to STDERR) will still show.

Try:
```

sh make.sh &> /dev/null

```

And see if that works.

---

### Post by sgy on 2011-07-12
That did it, it works now.

I should have thought to try that.

Thank you.

---

