---
title: "chromium dev build page &quot;problem&quot;"
date: 2009-08-19
forum: General Help
---

### Post by Soul-Sing on 2009-08-19
Hi,

I installed chromium on jaunty via the welknown ppa in launchpad.
Now I want to get rid of the =dev build= page, which automag. startsup. I tried several options to stop this but it keeps starting up.
Does someone know how to stop this?

---

### Post by sigurnjak on 2009-08-29
I would also like to know ! I know it is early in the development , but c'mon   how many times do we need to see darn warning !

---

### Post by darco on 2009-08-29
Try this....

[http://ubuntuforums.org/showpost.php?p=7813625&postcount=166](http://ubuntuforums.org/showpost.php?p=7813625&postcount=166)

darco

---

### Post by sigurnjak on 2009-08-30
thank for a lead , friend ! 
This is how i got to open my home page on start and avoid about:linux-splash :
chromium-browser --enable-plugins [http://www.google.ca/](http://www.google.ca/)

I have added this in my menu shortcut . 

In this case Google is my home page !

---

### Post by 16sinker on 2009-09-02
> **darco said:**
> Try this....

[http://ubuntuforums.org/showpost.php?p=7813625&postcount=166](http://ubuntuforums.org/showpost.php?p=7813625&postcount=166)

darco

I used the suggested solution to rid myself of the about:linux-splash page on opening, but now Chromium opens with the new tab page instead of my Google classic homepage and the Google homepage is set under options as my preferred homepage. Any suggestion?

---

### Post by sigurnjak on 2009-09-02
chromium-browser --enable-plugins [http://www.google.com/](http://www.google.com/)

Put this line in your chrome shortcut and it will start with google

---

### Post by 16sinker on 2009-09-02
Correction. I see that the launch command provided was the command to open "new tab." I need the command to launch Chromium with the Google classic homepage. Anybody?

---

### Post by 16sinker on 2009-09-02
> **sigurnjak said:**
> chromium-browser --enable-plugins [http://www.google.com/](http://www.google.com/)

Put this line in your chrome shortcut and it will start with google

Thank you. Please disregard my last post.

---

### Post by sigurnjak on 2009-09-02
You are welcome !:D

---

### Post by Czar on 2009-09-19
> **16sinker said:**
> I used the suggested solution to rid myself of the about:linux-splash page on opening, but now Chromium opens with the new tab page instead of my Google classic homepage and the Google homepage is set under options as my preferred homepage. Any suggestion?

Thanks!  Adding `chrome://newtab` is better then the meh "Chromium Dev Build" tab.

---

