---
title: "Scripting in 10.04 substantially different.  Things broke."
date: 2010-04-24
forum: General Help
---

### Post by outleradam on 2010-04-24
I have  a script which I designed on 9.04.  It worked for 9.10 and now  it does not work on development release.  For some reason it only works every 20th time.  It will reset itself until it finally works. Then when it does work, the cat command does not process the "/t"s in the code.

my script is mythicalLibrarian, you can find references here:
[http://wiki.xbmc.org/?title=MythicalLibrarian](http://wiki.xbmc.org/?title=MythicalLibrarian)
[http://forum.xbmc.org/search.php?searchid=5764194](http://forum.xbmc.org/search.php?searchid=5764194)
[http://code.google.com/p/mythicallibrarian/](http://code.google.com/p/mythicallibrarian/)

I Need some help.  The following code is supposed to auto-install mythicalLibrarian and it works on 9.10, but not on the development release. The following code will create the following
~/.mythicalLibrarian
/var/www/mythical-rss
/usr/local/bin/mythicalLibrarian
/usr/local/bin/librarian-notify-send

Here is the auto-installer i recommend to my users, there are many ways, but this is easiest.
```
 sudo apt-get install curl && mkdir ~/.mythicalLibrarian && mkdir ~/.mythicalLibrarian/mythicalSetup && cd ~/.mythicalLibrarian/mythicalSetup
curl http://mythicallibrarian.googlecode.com/svn/trunk/mythicalSetup.sh>./mythicalSetup.sh
sudo chmod +x ./mythicalSetup.sh && sudo ./mythicalSetup.sh 
```There is no malicious software here.  I need help making this work on 10.04.  I'm feeling as lost as when I first started using the terminal.

---

### Post by KeyserSoze93 on 2010-04-24
> **outleradam said:**
> I have  a script which I designed on 9.04.  It worked for 9.10 and now  it does not work on development release.  For some reason it only works every 20th time.  It will reset itself until it finally works. Then when it does work, the cat command does not process the "/t"s in the code.

my script is mythicalLibrarian, you can find references here:
[http://wiki.xbmc.org/?title=MythicalLibrarian](http://wiki.xbmc.org/?title=MythicalLibrarian)
[http://forum.xbmc.org/search.php?searchid=5764194](http://forum.xbmc.org/search.php?searchid=5764194)
[http://code.google.com/p/mythicallibrarian/](http://code.google.com/p/mythicallibrarian/)

I Need some help.  The following code is supposed to auto-install mythicalLibrarian and it works on 9.10, but not on the development release. The following code will create the following
~/.mythicalLibrarian
/var/www/mythical-rss
/usr/local/bin/mythicalLibrarian
/usr/local/bin/librarian-notify-send

Here is the auto-installer i recommend to my users, there are many ways, but this is easiest.
```
 sudo apt-get install curl && mkdir ~/.mythicalLibrarian && mkdir ~/.mythicalLibrarian/mythicalSetup && cd ~/.mythicalLibrarian/mythicalSetup
curl http://mythicallibrarian.googlecode.com/svn/trunk/mythicalSetup.sh>./mythicalSetup.sh
sudo chmod +x ./mythicalSetup.sh && sudo ./mythicalSetup.sh 
```There is no malicious software here.  I need help making this work on 10.04.  I'm feeling as lost as when I first started using the terminal.

No idea why it has ceased to work, I would hack the code to be a bit simpler from the get go:

```

mkdir -p ~/.mythicalLibrarian/mythicalSetup &&
cd ~/.mythicalLibrarian/mythicalSetup

wget "http://mythicallibrarian.googlecode.com/svn/trunk/mythicalSetup.sh"

bash mythicalSetup.sh

```

I'm still running 8.04, so I can't attest this version's efficacy, but I see nothing in there which should cough up an error.

---

### Post by outleradam on 2010-04-24
man...  that few lines of code installs over 2000 lines of bash which is not working.

Was there any changes to "cat" or "echo" recently? and how do I get them working the way they used to?

---

### Post by jobix on 2010-04-25
Put this line at the top of your script:

> set -x

That should tell you the steps it executes before it fails and you'll know where exactly it's failing. I doubt it's anything to do with cat or echo.

---

### Post by gmargo on 2010-04-25
Why you are trying edit the mythicalLibrarian.sh file with the replace command?  It's trashing the script.

---

### Post by prodigy_ on 2010-04-25
Like **jobix** said, use xtrace (set -x) to see what's happening. For more readability, redirect stderr to a file: ```
exec 2>/some_path/some_file
```

Personally, I haven't noticed any differences in 10.04, though I use sh, not bash.

---

### Post by asmoore82 on 2010-04-25
```
cat "./mythicalLibrarian.sh" | replace "\t" "\\\t " \\ \\\\ >"./mythicalLibrarian.sh"
```
^^you cannot reliably read from and write to the same file concurrently
Sometimes it will work and sometimes it won't.

The simple fix would be something like this:
```
cat "./mythicalLibrarian.sh" | replace "\t" "\\\t " \\ \\\\ >tmp
mv -f tmp "./mythicalLibrarian.sh"
```

A better solution would be a an "inplace" option whereby the
"replace" utility is made aware that it is editing a single file.
The standard utility `sed` has such an option: `-i`

I've never heard of `replace` before and don't have it on my system,
but googling "man replace" came up with this: [**_[COLOR="Purple"]http://linux.die.net/man/1/replace[/COLOR]_**]("http://linux.die.net/man/1/replace").

^^If that holds true, you should do this:
```
replace "\t" "\\\t " \\ \\\\ -- "./mythicalLibrarian.sh"
```

----------------

Also, I have some advice about this section:
```
startwrite=0
test -f ./librarian && rm -f ./librarian
while read line
do
    test "$line" = "########################## USER JOBS############################" && let startwrite=$startwrite+1
    if [ $startwrite = 2 ]; then
        echo -e "$line" >> ./librarian
        echo $startwrite
    fi
done <./mythicalLibrarian.sh
```

For clarity and consistency...
I would move that "header" line with all the hash marks into a variable.
I would refrain from using the `test && do` construct.
I would use the BASH math notation "((...))" instead of `let`
You should use `-eq` instead of `=` when testing for integer equality
I would use more quotation marks - around all assignment and echos.

But the more meaty advice is this - this one actually comes from experience.
I used the `>>` redirect in an if statement in a while loop for a script
not too long ago and eventually exposed a bug:
[B]You have no real guarantee that the file even exists at all after the loop
is complete[/B]. A better solution is to put the output redirect at the end
of the loop on the "done" line - right beside the input redirect.
Another quirk of this method is that it is slightly more efficient -
because the shell won't open the file for appending and close it for
**every** trip through the loop. It will be opened only once and truncated
if it already exists, so you can eliminate the initial test for it altogether.

Now this is slightly more complex in your situation because you have
other `echo` statements in the loop that shouldn't be directed to the file.
So you could use an explicitly numbered file descriptor. If you leave the number out,
1 is assumed which is stdout, 2 is stderr, but 3 and up are open for use anytime.
```
startwrite=[COLOR="Purple"]"0"[/COLOR]
[COLOR="Purple"]userjobs="########################## USER JOBS############################"[/COLOR]
while read line
do
    [COLOR="Purple"]if [ "$line" = "$userjobs" ]; then
        (( ++startwrite ))
    fi[/COLOR]
    if [ [COLOR="Purple"]"$startwrite" -eq "2"[/COLOR] ]; then
        echo -e "$line" [COLOR="Purple"]1>&3 #redirect to 3[/COLOR]
        echo [COLOR="Purple"]"$startwrite"[/COLOR]
    fi
done <./mythicalLibrarian.sh [COLOR="Purple"]3>./librarian[/COLOR]
```

So, this change will be slightly more efficient and have the welcomed
side effect that the file will always be created, but may be empty.

If that other echo in your loop is only for debugging, which it looks like it is,
you could get rid of the "redirect magic" with #3 and simply send it to stderr - "#2"
Then you could redirect the "librarian" file from stdout and it looks more natural...
```
startwrite="0"
userjobs="########################## USER JOBS############################"
while read line
do
    if [ "$line" = "$userjobs" ]; then
        (( ++startwrite ))
    fi
    if [ "$startwrite" -eq "2" ]; then
        echo -e "$line"
        echo "$startwrite" [COLOR="Purple"]1>&2 #stderr[/COLOR]
    fi
done <./mythicalLibrarian.sh [COLOR="Purple"]>./librarian[/COLOR]
```

If you take this advice, or maybe even if you don't, you can condense this
later operation:
```
cat ./mythicalSetup >./mythicalLibrarian
cat ./librarian >>./mythicalLibrarian
```
to this:
```
cat ./mythicalSetup ./librarian >./mythicalLibrarian
```

Note that in your code as it is, it's possible for a specially crafted "mythicalLibrarian.sh"
file to expose a bug where you are trying to`cat` a non-existent "librarian" file
because of no or not enough "$userjobs" found.

---

### Post by outleradam on 2010-04-27
The replace command works reliably. Every single time. The mythicalLibrarian SVN distribution system works great!  I've been using it for months with no problems to update 3 computers at my place, and my users have used it without a hitch until recently.

Actually the problem was a recent update to "sudo".  Aparently they've updated the sudo command so that a script running under sudo can no longer cat a file back onto itself.   ie...

sudo script.sh
```

cat script.sh > script.sh

```
does not rewrite script.sh.  it works as root, but not sudo root.

The soloution was to 
```

cat file1>file2
rm file1
mv file2 file1

```

The problem is resolved now.

---

### Post by outleradam on 2010-04-27
If you ran the script then you should have installed the dependencies required for the replace command.

The reason it has to be replaced is that the SVN is a actual working copy which I am running on my computer. 

1 Working copy gets uploaded to the SVN.
2. User downloads SVN/stable
3. Working copy gets tabs and \'s replaced with echo friendly characters
4. working copy is read until just past user settings (echo strips all tabs and spaces so the previous \s help)
5. mythicalSetup asks user questions and determines settings wile builiding ./mythicalLibrarian
6. previously stripped code portion is then reinserted into ./mythicalLibrarian 

So the final result is it is the program which was running on my computer, but with their settings.  Different computers require different settings.   Is there a better way to do this?   Instead of stripping it down on my end, I just have their computer do the work and I get to be lazy.   It requires preservation of tabs and "\"s though.

Is there a better way?

---

### Post by outleradam on 2010-04-27
On a side note, asmoore82, you said 
```

(( ++var )) 
```
is the bash way, but I stayed away from that because it's annotated in the logs as the "C style" so I went with the bash style.  I will go with the C style as it is preferred.

---

