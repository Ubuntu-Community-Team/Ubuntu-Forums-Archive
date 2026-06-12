---
title: "Can I copyright bash scripts?"
date: 2010-04-14
forum: General Help
---

### Post by wrix on 2010-04-14
Hello, I have created some bash programs (scripts). Can they be copyrighted, if yes then is it mandatory to use GPL as bash (the interpreter) is GPL'd or they can be under any license, even close source? please help me in this regards. Thanks.

---

### Post by prodigy_ on 2010-04-14
/facepalm

---

### Post by Miyavix3 on 2010-04-14
Why would you want to copywrite something open-source? You can't compile a bash script, you know.

---

### Post by cong06 on 2010-04-14
Just so you can understand everyone's reaction, let's think for a bit.


Bash scripts are scripts. Their code is in human readable form so that a programmer can easily type, and then the next second have a shell run the language. Ruby, Bash, perl, python, they all work this way.
These languages are called Scripting languages because they don't need a compiler. It is impossible to make it so that a user can run this script without being able to read the contents (unless you have control of his computer, and have specific permissions on the file)

Compilers take this human readable language, and turn it into something that only machines can understand. For example, C and Java are compiled languages.

The term "Open-Source" means that the source is available. With Scripting Languages, this is the only option.
The term "Closed-Source" means that all the end user is allowed to see is compiled code, which I would assume, they can not understand.

---

### Post by chessnerd on 2010-04-14
> **Miyavix3 said:**
> Why would you want to copywrite something open-source? You can't compile a bash script, you know.

You can copyright an essay even though the entire things is "open-source." The openness of the source doesn't change the copyright. Minix had a restrictive license in the late 80s/early 90s even though the entire thing was open-source. 

Open-source and copyleft are not the same thing.

To the original poster:

From my understanding you can license your bash script under any license you want. If you wrote it then you are allowed to restrict the copying of your scripts under standard copyright law. Will this be harder to enforce than with standard, binary programs? Yes. But it is possible under copyright law.

They cannot, however be "closed source" because, as mentioned, scripts are human-readable.

---

### Post by mobilediesel on 2010-04-14
> **wrix said:**
> Hello, I have created some bash programs (scripts). Can they be copyrighted, if yes then is it mandatory to use GPL as bash (the interpreter) is GPL'd or they can be under any license, even close source? please help me in this regards. Thanks.

The script itself wouldn't have to be the same license as Bash. I usually use the [Creative Commons Attribution-Share Alike 3.0 Unported License]("http://creativecommons.org/licenses/by-sa/3.0/").

That license basically says share it and share any modifications. I mostly do that just because if someone wants to use it and modify it there's no real way to stop them.

A Bash script is really just a string of commands you can simply enter at a command prompt. That means the only way to truly have it "closed source" is to never let anyone see or use it.

> **chessnerd said:**
> They cannot, however be "closed source" because, as mentioned, scripts are human-readable.

Yeah, I totally didn't read the whole thread before replying so I'm not even the second one to point this out. :D

---

### Post by hawthornso23 on 2010-04-14
Definitely you can copyright them. They are a creative work. They are automatically copyrighted as soon as you write 'em. And if you are not distributing them the GPL question doesn't even arise. 

Let's assume however that you set up a business selling bash scripts.

Does a bash script incorporate GPL content? I'd say no - not unless you compile it. Until then it only names GPL components as distinct from incorporating them. Are you planning to compile these bash scripts? That isn't what you usually do with bash scripts. If they were compiled however I'd say the answer was yes.

Conclusion: I don't believe you are obliged to GPL uncompiled bash scripts. License them however you please. However note that the main obligation that the GPL would impose on you would be to distribute the source code ... and bash scripts ARE source code ... so that wouldn't exactly be a hard obligation to meet!


This is not legal advice - blah blah blah - buggerit - talk to a real lawyer - millennium hand and shrimp

---

### Post by Miyavix3 on 2010-04-16
> **chessnerd said:**
> You can copyright an essay even though the entire things is "open-source."

oh you

---

### Post by Chronon on 2010-04-16
> **hawthornso23 said:**
> Definitely you can copyright them. They are a creative work. They are automatically copyrighted as soon as you write 'em. And if you are not distributing them the GPL question doesn't even arise. 

Let's assume however that you set up a business selling bash scripts.

Does a bash script incorporate GPL content? I'd say no - not unless you compile it. Until then it only names GPL components as distinct from incorporating them. Are you planning to compile these bash scripts? That isn't what you usually do with bash scripts. If they were compiled however I'd say the answer was yes.

Conclusion: I don't believe you are obliged to GPL uncompiled bash scripts. License them however you please. However note that the main obligation that the GPL would impose on you would be to distribute the source code ... and bash scripts ARE source code ... so that wouldn't exactly be a hard obligation to meet!


This is not legal advice - blah blah blah - buggerit - talk to a real lawyer - millennium hand and shrimp

I agree.  The availability of the source does nothing to force the author to select a particular distribution license.  

Of course, copyright only protects form.  You could change the appearance of the script and avoid copyright violation pretty easily.

---

### Post by ad_267 on 2010-04-16
Closed source doesn't mean that no one can ever see the code. A lot of commercial software providers will allow access to their source code for a fee.

And all code released under an open source license is copyrighted. When you release code under an open source license you are saying that the copyright belongs to you but that people can use it under certain conditions. So if you think you can't copyright something and give out the source code you're completely wrong.

Think about it, what's the point in copyrighting something that no one is ever going to see?

To answer the original question, yes you can copyright your scripts and no they don't have to be released under any particular license.

---

### Post by iponeverything on 2010-04-16
> **wrix said:**
> Hello, I have created some bash programs (scripts). Can they be copyrighted, if yes then is it mandatory to use GPL as bash (the interpreter) is GPL'd or they can be under any license, even close source? please help me in this regards. Thanks.

Sure. No need to GPL. Wouldn't you feel a little bit guilty though, I mean almost everything you used to create your "programs", with the exception of your brain -- is GPL. 

Anyway, good luck with it regardless.

---

### Post by The Mishanator on 2010-04-24
have a look at a program called shc.. it converts your scripts to c code.

---

### Post by The Mishanator on 2010-04-24
for example, the bash script: > #!/bin/bash

printf "Hello World!!!\n"gets converted to C source: > #if 0
    shc Version 3.8.7, Generic Script Compiler
    Copyright (c) 1994-2009 Francisco Rosales <frosal@fi.upm.es>

    shc -f /home/mikhail/Desktop/hello 
#endif

static  char data [] = 
#define      msg1_z    42
#define      msg1    ((&data[3]))
    "\020\125\270\254\177\011\075\306\067\350\276\104\251\210\205\065"
    "\170\045\312\101\341\251\245\120\247\024\001\340\310\135\143\026"
    "\034\337\060\376\122\050\172\160\021\270\040\342\253\151\046\012"
    "\307\346\071"
#define      pswd_z    256
#define      pswd    ((&data[106]))
    "\133\020\077\276\233\211\204\205\210\125\070\320\171\314\040\327"
    "\351\162\150\372\307\040\143\356\053\053\324\144\055\260\346\211"
    "\301\045\107\134\257\314\341\067\042\032\010\233\346\050\162\320"
    "\232\333\312\142\373\056\120\065\113\061\215\150\055\130\106\027"
    "\243\243\230\300\252\010\175\224\223\161\114\064\123\307\236\344"
    "\305\010\135\345\361\361\033\075\043\250\246\120\001\355\147\245"
    "\220\377\145\072\010\342\317\234\124\033\320\247\343\156\214\251"
    "\167\351\216\151\333\251\246\376\122\115\117\124\072\266\371\312"
    "\266\137\005\277\102\324\134\227\360\054\076\324\233\312\175\022"
    "\264\014\174\220\266\043\217\011\160\336\135\252\225\127\164\114"
    "\267\171\013\371\116\150\221\077\224\317\023\060\232\221\103\117"
    "\235\277\340\124\342\157\135\122\115\273\375\343\023\161\057\312"
    "\353\073\304\072\243\125\171\070\045\215\150\300\036\254\020\273"
    "\153\360\020\116\140\155\241\256\050\236\221\074\020\300\007\374"
    "\374\313\066\237\041\260\327\107\075\100\007\133\354\030\027\130"
    "\011\047\247\151\225\110\027\276\347\250\372\370\151\001\364\145"
    "\315\053\005\356\333\335\066\031\035\076\165\012\126\214\143\137"
    "\264\012\311\111\123\340\007\072\211\002\062\363\003\047\130\320"
    "\122\136\277\056\073\366\110\130\064\275\143\212\112\306\352\376"
    "\320\263\110\043\223\117\136\046\131\045\213\207\326\161\020\227"
    "\227\130\363\107\045\325\177\107\360\207\343\327\260\125\247\112"
    "\060\162\255\054\241\376\122"
#define      chk2_z    19
#define      chk2    ((&data[394]))
    "\302\366\364\253\355\342\155\150\117\157\155\172\106\366\311\151"
    "\227\361\014\202\372\117\222"
#define      chk1_z    22
#define      chk1    ((&data[422]))
    "\205\056\020\133\255\232\326\003\376\060\362\051\263\275\076\375"
    "\032\004\245\162\126\270\171\370\373\055\330\127\113\064\072\042"
#define      tst2_z    19
#define      tst2    ((&data[451]))
    "\057\301\044\306\101\320\373\250\201\061\300\273\012\215\346\243"
    "\263\161\264\273\253\075\335\355"
#define      date_z    1
#define      date    ((&data[473]))
    "\362"
#define      text_z    40
#define      text    ((&data[484]))
    "\133\372\155\355\214\124\330\022\202\351\323\010\105\234\307\270"
    "\006\111\160\060\234\107\212\135\166\100\035\045\057\302\230\156"
    "\355\164\234\314\275\312\024\234\312\063\037\366\273\350\050\263"
    "\315\252\155"
#define      shll_z    10
#define      shll    ((&data[525]))
    "\341\216\106\061\256\040\134\141\224\140\144\173"
#define      inlo_z    3
#define      inlo    ((&data[537]))
    "\151\007\047"
#define      msg2_z    19
#define      msg2    ((&data[542]))
    "\343\125\331\016\141\371\321\133\143\120\240\002\036\166\143\104"
    "\230\165\314\273\163\274\301\061\374"
#define      rlax_z    1
#define      rlax    ((&data[565]))
    "\357"
#define      xecc_z    15
#define      xecc    ((&data[566]))
    "\243\207\127\127\006\144\011\071\001\141\331\154\263\145\204\343"
    "\270"
#define      lsto_z    1
#define      lsto    ((&data[583]))
    "\142"
#define      tst1_z    22
#define      tst1    ((&data[587]))
    "\216\346\361\237\246\222\343\210\143\266\152\214\341\216\161\133"
    "\020\210\366\335\240\002\174\151\014\363"
#define      opts_z    1
#define      opts    ((&data[610]))
    "\142"/* End of data[] */;
#define      hide_z    4096
#define DEBUGEXEC    0    /* Define as 1 to debug execvp calls */
#define TRACEABLE    0    /* Define as 1 to enable ptrace the executable */

/* rtc.c */

#include <sys/stat.h>
#include <sys/types.h>

#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <unistd.h>

/* 'Alleged RC4' */

static unsigned char stte[256], indx, jndx, kndx;

/*
 * Reset arc4 stte. 
 */
void stte_0(void)
{
    indx = jndx = kndx = 0;
    do {
        stte[indx] = indx;
    } while (++indx);
}

/*
 * Set key. Can be used more than once. 
 */
void key(void * str, int len)
{
    unsigned char tmp, * ptr = (unsigned char *)str;
    while (len > 0) {
        do {
            tmp = stte[indx];
            kndx += tmp;
            kndx += ptr[(int)indx % len];
            stte[indx] = stte[kndx];
            stte[kndx] = tmp;
        } while (++indx);
        ptr += 256;
        len -= 256;
    }
}

/*
 * Crypt data. 
 */
void arc4(void * str, int len)
{
    unsigned char tmp, * ptr = (unsigned char *)str;
    while (len > 0) {
        indx++;
        tmp = stte[indx];
        jndx += tmp;
        stte[indx] = stte[jndx];
        stte[jndx] = tmp;
        tmp += stte[indx];
        *ptr ^= stte[tmp];
        ptr++;
        len--;
    }
}

/* End of ARC4 */

/*
 * Key with file invariants. 
 */
int key_with_file(char * file)
{
    struct stat statf[1];
    struct stat control[1];

    if (stat(file, statf) < 0)
        return -1;

    /* Turn on stable fields */
    memset(control, 0, sizeof(control));
    control->st_ino = statf->st_ino;
    control->st_dev = statf->st_dev;
    control->st_rdev = statf->st_rdev;
    control->st_uid = statf->st_uid;
    control->st_gid = statf->st_gid;
    control->st_size = statf->st_size;
    control->st_mtime = statf->st_mtime;
    control->st_ctime = statf->st_ctime;
    key(control, sizeof(control));
    return 0;
}

#if DEBUGEXEC
void debugexec(char * sh11, int argc, char ** argv)
{
    int i;
    fprintf(stderr, "shll=%s\n", sh11 ? sh11 : "<null>");
    fprintf(stderr, "argc=%d\n", argc);
    if (!argv) {
        fprintf(stderr, "argv=<null>\n");
    } else { 
        for (i = 0; i <= argc ; i++)
            fprintf(stderr, "argv[%d]=%.60s\n", i, argv[i] ? argv[i] : "<null>");
    }
}
#endif /* DEBUGEXEC */

void rmarg(char ** argv, char * arg)
{
    for (; argv && *argv && *argv != arg; argv++);
    for (; argv && *argv; argv++)
        *argv = argv[1];
}

int chkenv(int argc)
{
    char buff[512];
    unsigned long mask, m;
    int l, a, c;
    char * string;
    extern char ** environ;

    mask  = (unsigned long)&chkenv;
    mask ^= (unsigned long)getpid() * ~mask;
    sprintf(buff, "x%lx", mask);
    string = getenv(buff);
#if DEBUGEXEC
    fprintf(stderr, "getenv(%s)=%s\n", buff, string ? string : "<null>");
#endif
    l = strlen(buff);
    if (!string) {
        /* 1st */
        sprintf(&buff[l], "=%lu %d", mask, argc);
        putenv(strdup(buff));
        return 0;
    }
    c = sscanf(string, "%lu %d%c", &m, &a, buff);
    if (c == 2 && m == mask) {
        /* 3rd */
        rmarg(environ, &string[-l - 1]);
        return 1 + (argc - a);
    }
    return -1;
}

#if !TRACEABLE

#define _LINUX_SOURCE_COMPAT
#include <sys/ptrace.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <fcntl.h>
#include <signal.h>
#include <stdio.h>
#include <unistd.h>

#if !defined(PTRACE_ATTACH) && defined(PT_ATTACH)
#    define PTRACE_ATTACH    PT_ATTACH
#endif
void untraceable(char * argv0)
{
    char proc[80];
    int pid, mine;

    switch(pid = fork()) {
    case  0:
        pid = getppid();
        /* For problematic SunOS ptrace */
#if defined(__FreeBSD__)
        sprintf(proc, "/proc/%d/mem", (int)pid);
#else
        sprintf(proc, "/proc/%d/as",  (int)pid);
#endif
        close(0);
        mine = !open(proc, O_RDWR|O_EXCL);
        if (!mine && errno != EBUSY)
            mine = !ptrace(PTRACE_ATTACH, pid, 0, 0);
        if (mine) {
            kill(pid, SIGCONT);
        } else {
            perror(argv0);
            kill(pid, SIGKILL);
        }
        _exit(mine);
    case -1:
        break;
    default:
        if (pid == waitpid(pid, 0, 0))
            return;
    }
    perror(argv0);
    _exit(1);
}
#endif /* !TRACEABLE */

char * xsh(int argc, char ** argv)
{
    char * scrpt;
    int ret, i, j;
    char ** varg;

    stte_0();
     key(pswd, pswd_z);
    arc4(msg1, msg1_z);
    arc4(date, date_z);
    if (date[0] && (atoll(date)<time(NULL)))
        return msg1;
    arc4(shll, shll_z);
    arc4(inlo, inlo_z);
    arc4(xecc, xecc_z);
    arc4(lsto, lsto_z);
    arc4(tst1, tst1_z);
     key(tst1, tst1_z);
    arc4(chk1, chk1_z);
    if ((chk1_z != tst1_z) || memcmp(tst1, chk1, tst1_z))
        return tst1;
    ret = chkenv(argc);
    arc4(msg2, msg2_z);
    if (ret < 0)
        return msg2;
    varg = (char **)calloc(argc + 10, sizeof(char *));
    if (!varg)
        return 0;
    if (ret) {
        arc4(rlax, rlax_z);
        if (!rlax[0] && key_with_file(shll))
            return shll;
        arc4(opts, opts_z);
        arc4(text, text_z);
        arc4(tst2, tst2_z);
         key(tst2, tst2_z);
        arc4(chk2, chk2_z);
        if ((chk2_z != tst2_z) || memcmp(tst2, chk2, tst2_z))
            return tst2;
        if (text_z < hide_z) {
            /* Prepend spaces til a hide_z script size. */
            scrpt = malloc(hide_z);
            if (!scrpt)
                return 0;
            memset(scrpt, (int) ' ', hide_z);
            memcpy(&scrpt[hide_z - text_z], text, text_z);
        } else {
            scrpt = text;    /* Script text */
        }
    } else {            /* Reexecute */
        if (*xecc) {
            scrpt = malloc(512);
            if (!scrpt)
                return 0;
            sprintf(scrpt, xecc, argv[0]);
        } else {
            scrpt = argv[0];
        }
    }
    j = 0;
    varg[j++] = argv[0];        /* My own name at execution */
    if (ret && *opts)
        varg[j++] = opts;    /* Options on 1st line of code */
    if (*inlo)
        varg[j++] = inlo;    /* Option introducing inline code */
    varg[j++] = scrpt;        /* The script itself */
    if (*lsto)
        varg[j++] = lsto;    /* Option meaning last option */
    i = (ret > 1) ? ret : 0;    /* Args numbering correction */
    while (i < argc)
        varg[j++] = argv[i++];    /* Main run-time arguments */
    varg[j] = 0;            /* NULL terminated array */
#if DEBUGEXEC
    debugexec(shll, j, varg);
#endif
    execvp(shll, varg);
    return shll;
}

int main(int argc, char ** argv)
{
#if DEBUGEXEC
    debugexec("main", argc, argv);
#endif
#if !TRACEABLE
    untraceable(argv[0]);
#endif
    argv[1] = xsh(argc, argv);
    fprintf(stderr, "%s%s%s: %s\n", argv[0],
        errno ? ": " : "",
        errno ? strerror(errno) : "",
        argv[1] ? argv[1] : "<null>"
    );
    return 1;
}
it may not be the most efficient way, but it works

---

