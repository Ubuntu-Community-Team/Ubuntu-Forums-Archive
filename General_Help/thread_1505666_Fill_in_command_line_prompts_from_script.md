---
title: "Fill in command line prompts from script"
date: 2010-06-09
forum: General Help
---

### Post by lordofhumankind on 2010-06-09
I have set up an ssh server for myself and a friend to work on a project. It is configured to use password authentication, but I am somewhat uncomfortable giving him my password to get the files. I was wondering if there was any way to have a script that logs him on, filling in the password at the prompt. So that when "ssh xxxx@xxxxx" is run, the script fills in the prompt for the password rather than him filling it in.
Of course he still could find the file within the script before it is run, but knowing his somewhat ADD nature it seems unlikely. Any help is appreciated.

---

### Post by bashologist on 2010-06-09
I don't know what you're trying exactly, but would a samba server work maybe? You could then deny everyone access except the hosts you allow. You could share your project that way or does he need a command prompt?

---

