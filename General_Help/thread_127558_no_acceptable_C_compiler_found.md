---
title: "no acceptable C compiler found"
date: 2006-02-09
forum: General Help
---

### Post by shams2 on 2006-02-09
hi,
i am using ubuntu, when i want to install the packages from sources, with ./configure this is the error:
Checking how to run the C pre-processor...
configure: cannot find out how to run the C pre-processor; set the environment variable CPP and try again
and 
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
which packges i sould install for C compiler?

---

### Post by Seaman on 2006-02-09
And what does 'config.log' tell you?

---

### Post by jmvbxx on 2006-02-09
I have this exact same problem.  I'm using Ubuntu 5.1 and have tried to install two different applications w the same error.

Here is a portion of the config.log file:

configure:1718: error: C compiler cannot create  executables

Any assistance is greatly appreciated!!!

---

### Post by taurus on 2006-02-09
sudo apt-get install build-essential

---

### Post by jmvbxx on 2006-02-09
It worked!

Thank you so much!

---

