---
title: "How to modify keymapping of getty?"
date: 2009-10-05
forum: General Help
---

### Post by sswv on 2009-10-05
I am using PAM on Ubuntu 9.04, and some of the usernames in PAM/NSS are emails including an "@".

When login, I found "@" became a kill character that would kill all the characters one the left side.
I found the reason at [http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-5.html](http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-5.html) :
"The default erase and kill characters are # and @, as in good old Unix Version 6"
"At the first attempt, you are talking to getty. At the second attempt, you are talking to login, a different program."
That is to say, the keymapping of getty led to it.

How to modify keymapping of getty in order to input "@" when login?
It is not OK to use stty after login because stty is effective for current tty only.

Redhat and CentOS do not have this problem, and "@" can be inputted in getty directly.

When I "man getty", Ubuntu shows like this: [http://manpages.ubuntu.com/manpages/jaunty/en/man8/getty.8.html](http://manpages.ubuntu.com/manpages/jaunty/en/man8/getty.8.html)
It mentions that in "agetty", "The following special  characters  are  recognized: @ and Control-U (kill); #, DEL and back space (erase); carriage return and line  feed  (end of line)."
But it does not say how to disable this non-standard feature.

Thanks.

---

### Post by sswv on 2009-10-06
I solved it by myself:
Use mingetty (what CentOS uses) instead of agetty.

---

