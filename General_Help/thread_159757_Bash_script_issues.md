---
title: "Bash script issues"
date: 2006-04-13
forum: General Help
---

### Post by apsalyers on 2006-04-13
I'm trying to port over some of my old bash scripts from Redhat to my new Ubuntu/Kubuntu systems.  I have located the appropriate bash location, but none of the scripts seem to work.  Even the simpliest test scripts throw the same errors.  For example the following simple script:

#!/bin/bash
#This script says hello
echo Hello World
done

Throws the error, "/bin/bash^M: bad interpreter: No such file or directory

I try it with and without sudo, and with and without the "done" command at the end.  No change.

I'm sure the solution is some little quirk that i'm going to feel like a total and complete noob for asking, but this is driving me batty.

Any assistance appreciated, thanks in advance.

---

### Post by kingmonkey on 2006-04-13
it doesnt like done, try exit 0, and also "" around the "Hello World" would be better.

There are lots of sites about scripting in bash

---

### Post by apsalyers on 2006-04-13
I have read several of the sites, but to no avail with the "bad interpreter" message.  Thanks for the info regarding exit 0.

---

### Post by kingmonkey on 2006-04-13
try #!/bin/sh instead of bash to see if that makes a difference?

---

### Post by apsalyers on 2006-04-13
Same error i'm afraid, thanks for the try.

---

### Post by kingmonkey on 2006-04-13
I think that somehow you have got a weird ^M character on your interpreter line.

---

### Post by stuporglue on 2006-04-13
> /bin/bash^M
 and
> I think that somehow you have got a weird ^M character on your interpreter line.

I think that's what happened. Did you ever transfer/edit/view these files on Windows?  I think it's your line endings. Make a backup of your file before trying this...

perl -p -i -e s/\n/\r/g yourfilename

replaces all instances of \n (newline) with \r (other type of newline)

(replace format is s/formerstring/replacewiththis/g

Sadly, I don't know enough about it to know what's called what. 

Here's a page with a bit more about it, in relation to Vim 
[http://www.vim.org/tips/tip.php?tip_id=145](http://www.vim.org/tips/tip.php?tip_id=145)

Hope that helps

---

### Post by apsalyers on 2006-04-13
Yet another reason to growl at Windows.  Thanks, hat was the problem.  I had made some changes to the scripts using Ultraedit from my windows machine at work.  I carry my main script on a USB key.  I rewrote two of the shorter scripts directly in Kate and all worked fine.  Thanks again.

---

### Post by xenmax on 2006-04-13
Actually i had this issue once before. I tried 
```
sed -e 's/\r/\n/' < foo.sh > foo1.sh
``` which seemed to work at a level for me. Back-up one of your scripts and see if this works. I just used it once or twice. So i am not aware of complications/exceptions, but should generally work.
I do not know if windows uses \r or \n or whatever - difference between the two is small if any and i dont even remember what it is - i was just experimenting and this seemed to work for me.

---

