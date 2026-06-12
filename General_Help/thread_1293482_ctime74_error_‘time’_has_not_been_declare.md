---
title: "ctime:74: error: ‘::time’ has not been declare"
date: 2009-10-17
forum: General Help
---

### Post by miroslav_karpis on 2009-10-17
Hi,

**please** can you help me with this? Everything worked correctly (compiling) and suddenly I got this error (in the program I didn't change anything), but most probably I did something with global include path in a terminal?...no idea :confused:

thank you in advance,
Miro

---

### Post by miroslav_karpis on 2009-10-17
uff, so I figured it out...the problem was that I changed by accident the time.h file 

/* Return the current time and put it in *TIMER if TIMER is not NULL.  */
extern time_t **time** (time_t *__timer) __THROW;


to

/* Return the current time and put it in *TIMER if TIMER is not NULL.  */
extern time_t **datetime** (time_t *__timer) __THROW;

of course **time** is correct

---

