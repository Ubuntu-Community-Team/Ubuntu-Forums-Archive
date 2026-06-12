---
title: "Weird error message in karmic"
date: 2009-11-11
forum: General Help
---

### Post by scared0o0rabbit on 2009-11-11
Sometimes when the screen has blanked from inactivity and I move the mouse to bring the screen back I have a weird icon in the bar at the top that gives me an error message that says: Session active, not inhibited, screen idle.  It basically says I shouldn't be seeing it because my display server is broken.  I have no idea what this means, and it then tends to disappear eventually.  It hasn't seemed to cause any problems, but I'm not really sure what's up with it.  It's a fairly fresh install of karmic and I'm on a sony PCG-K15 Laptop.

It never did this to me in Jaunty, but has done it a few times in Karmic now.  Going to the link provided in the error message: [http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/) provides some clues, but I don't know if there's some setting I need to change.

It looks like it has something to do with power management.  Also of note is that I was never able to suspend my laptop in Jaunty, but I've now attempted to do it twice in Karmic and had it work once and then not work the second time, so I don't know if this is related.

---

### Post by rhy7s on 2009-11-17
I get this error as well in 9.10 installed on an Eee 901. Previousy in Janty the screen would blank and the only way to get it back was to suspend then resume. Now, in Karmic the screen dims but remains usable and the applet message referred to in the original post appears.

---

### Post by Mint Sharpie on 2009-11-17
I've started getting this too. I'm on an SL500 Thinkpad and just upgraded from Jaunty to Karmic. The message popped up yesterday and while I've never had problems hibernating or suspending, returning from idle has gotten rather annoying. If I let him go idle, he'll fade to black with the cursor still visible and responsive but not brightening again for a good ten seconds when I move the mouse or hit a key. This happens both on battery and AC power.

I'm also something of a newbie to the intricacies of Linux; I can use the terminal but need step-by-step instructions for anything more complicated than ssh. If there's a fix for this on the net already can somebody translate it into layman's terms for me, please?

---

### Post by fluffman86 on 2009-11-17
Just ignore it.  This message was added during testing because some laptops (like mine) were idle for the amount of time set in power management, then the screen would black (like I told it to), then it would immediately wake up.  To try and isolate the problem, the message was added to let people know that the issue was being worked on.

So if your screen actually blanks like it's supposed to, the message just hasn't gone away yet and can be ignored.

edit @Mint Sharpie: The above info is for the OP only.  Your laptop or install or configuration actually does appear to be broken.  Keep looking for a solution, and check for open bugs on launchpad.  If you can't find anything, open a new bug by doing:
ubuntu-bug devicekit-power

That will automatically send information about your system to launchpad so they can get it fixed.

Also, the reason it takes like 10 seconds to wake up, is because, again, during testing, people with screens like mine were sleeping and waking up *VERY* quickly.  So a delay was added to prevent that.  Now it's required to sleep 5 or 10 seconds if Ubuntu thinks there might be a problem.

---

### Post by Mint Sharpie on 2009-11-17
*sigh* Lovely... Thank you for the help, I'll file a bug report and keep poking around.

---

### Post by rb0171610 on 2009-11-17
> **Mint Sharpie said:**
> *sigh* Lovely... Thank you for the help, I'll file a bug report and keep poking around.That sounds like the appropriate plan of action for you, since reading the manual pages for patch seems too time consuming.

---

### Post by fluffman86 on 2009-11-17
@rb0912978625786: so you have a patch? why not post a link to it instead of just being a douche and telling him to patch the issue himself?

---

### Post by rb0171610 on 2009-11-17
> **fluffman86 said:**
> @rb0912978625786: so you have a patch? why not post a link to it instead of just being a douche and telling him to patch the issue himself?
You are calling me a douche in the forums? I do not have a link to the patch, the OP provided the link in her original post.  I am asking her to read the man pages for patch and/or install patch if it is not already. As I do not know if this will or will not fix her problem, I suggested that she backup the file she is trying to patch and read the manual pages for the patch program before trying to apply the patch.  If at that point, the OP can still not figure out how to apply a patch, she is free to post for more help.

---

### Post by Mint Sharpie on 2009-11-17
Woah guys, chill out. Like I said, I'm new at this stuff, I didn't even know that "patch" was a program. I'll read the man first and come back if I need more help.

And for future reference, I'm a she. =)

---

### Post by fluffman86 on 2009-11-17
I'm sorry.  I apologize.  I was kinda hasty in writing that.

The link that the OP posted is old.  All of the patches listed there have already been applied in Karmic.

---

### Post by rb0171610 on 2009-11-17
> **Mint Sharpie said:**
> Woah guys, chill out. Like I said, I'm new at this stuff, I didn't even know that "patch" was a program. I'll read the man first and come back if I need more help.

And for future reference, I'm a she. =)
Also, try  patch --help:
Usage: patch [OPTION]... [ORIGFILE [PATCHFILE]]

Input options:

  -p NUM  --strip=NUM  Strip NUM leading components from file names.
  -F LINES  --fuzz LINES  Set the fuzz factor to LINES for inexact matching.
  -l  --ignore-whitespace  Ignore white space changes between patch and input.

  -c  --context  Interpret the patch as a context difference.
  -e  --ed  Interpret the patch as an ed script.             
  -n  --normal  Interpret the patch as a normal difference.  
  -u  --unified  Interpret the patch as a unified difference.

  -N  --forward  Ignore patches that appear to be reversed or already applied.
  -R  --reverse  Assume patches were created with old and new files swapped.  

  -i PATCHFILE  --input=PATCHFILE  Read patch from PATCHFILE instead of stdin.

Output options:

  -o FILE  --output=FILE  Output patched files to FILE.
  -r FILE  --reject-file=FILE  Output rejects to FILE. 

  -D NAME  --ifdef=NAME  Make merged if-then-else output using NAME.
  -E  --remove-empty-files  Remove output files that are empty after patching.

  -Z  --set-utc  Set times of patched files, assuming diff uses UTC (GMT).
  -T  --set-time  Likewise, assuming local time.                          

  --quoting-style=WORD   output file names using quoting style WORD.
    Valid WORDs are: literal, shell, shell-always, c, escape.       
    Default is taken from QUOTING_STYLE env variable, or 'shell' if unset.

Backup and version control options:

  -b  --backup  Back up the original contents of each file.
  --backup-if-mismatch  Back up if the patch does not match exactly.
  --no-backup-if-mismatch  Back up mismatches only if otherwise requested.

  -V STYLE  --version-control=STYLE  Use STYLE version control.
        STYLE is either 'simple', 'numbered', or 'existing'.   
  -B PREFIX  --prefix=PREFIX  Prepend PREFIX to backup file names.
  -Y PREFIX  --basename-prefix=PREFIX  Prepend PREFIX to backup file basenames.
  -z SUFFIX  --suffix=SUFFIX  Append SUFFIX to backup file names.              

  -g NUM  --get=NUM  Get files from RCS etc. if positive; ask if negative.

Miscellaneous options:

  -t  --batch  Ask no questions; skip bad-Prereq patches; assume reversed.
  -f  --force  Like -t, but ignore bad-Prereq patches, and assume unreversed.
  -s  --quiet  --silent  Work silently unless an error occurs.
  --verbose  Output extra information about the work being done.
  --dry-run  Do not actually change any files; just print what would happen.
  --posix  Conform to the POSIX standard.

  -d DIR  --directory=DIR  Change the working directory to DIR first.
  --binary  Read and write data in binary mode (no effect on this platform).

  -v  --version  Output version info.
  --help  Output this help.

---

### Post by rb0171610 on 2009-11-17
> **fluffman86 said:**
> I'm sorry.  I apologize.  I was kinda hasty in writing that.

The link that the OP posted is old.  All of the patches listed there have already been applied in Karmic.
Apology accepted.

---

### Post by evPaseo on 2009-11-18
Mint - I have also been receiving this error message. If you are able to find a solution, please post it for the rest of us.
-- Thanks

---

