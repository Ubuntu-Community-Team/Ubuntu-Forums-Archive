---
title: "how to break up a large folder of jpegs into multiple smaller folders?"
date: 2011-03-01
forum: General Help
---

### Post by tnc on 2011-03-01
Hello and Thanks for looking!

I have a folder with some 25,000 jpegs in it.  Our old computer here simply chokes on it.  (This is the thread that shows how I got myself to this point: [http://ubuntuforums.org/showthread.php?t=1692117&goto=newpost](http://ubuntuforums.org/showthread.php?t=1692117&goto=newpost)  )


How would a person go about breaking this folder up into smaller, more manageable sized folders?  I'm not sure where even to start...

The goal is to separate out the jpegs (roughly 1000 or so) that are actually our pictures from the miscellaneous rubbish.

Thanks.
Tim

---

### Post by nothingspecial on 2011-03-01
To do it without viewing them there would need to be some kind of unique attribute to those files.


Is there one?

---

### Post by tnc on 2011-03-01
Well now, size would be the only real difference I guess.  Otherwise there is, as far as Ubuntu is concerned, no difference between our pictures and leftover jpegs from browsing and such. 

Your question then makes my brain unlock :) 
This command should work to separate off a bit at a time, right?  Just use increasing sizes in multiple commands:

find /home/tnc/recovered/recoveredjpg/ -type f -size -2000c -print -exec mv -f {} \;

Whaddya think?

Thanks!
Tim

---

### Post by nothingspecial on 2011-03-02
That would work.

Don't forget to specify where you want them moving to.

Also, if the file permissions have been preserved you could use the -user option.

---

