---
title: "gcc fails to compile vfdecrypt - %lu"
date: 2010-02-03
forum: General Help
---

### Post by HuckBerry on 2010-02-03
I've used linux for a quite a while and have compiled a small number of applications from source for one reason or another, however this on has me stumped. The program is vfdecrypt which if you are unaware is used to decrypt (among other things) .dmg files such as those found on apple hardware.

Here are the relevant definitions:
```
...
typedef struct {
  unsigned char sig[8];
  uint32_t version;
...
  uint32_t blocksize;
  uint64_t datasize;
  uint64_t dataoffset;
...
}

```and here is the offending line of code:
```
void dump_v2_header(void *hdr) {
  cencrypted_v2_pwheader *pwhdr = (cencrypted_v2_pwheader *) hdr;

  fprintf(stderr, "sig\t%8s\n", pwhdr->sig);
  fprintf(stderr, "blocksize\t%lu\n", pwhdr->blocksize); //<---------- This line
  fprintf(stderr, "datasize\t%llu\n", pwhdr->datasize);
  fprintf(stderr, "dataoffset\t%llu\n", pwhdr->dataoffset);
...
}
```gcc reports this error:
```
/.../src/vfdecrypt.c: In function ‘dump_v2_header’:
/.../src/vfdecrypt.c:138: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 3 has type ‘uint32_t’

```Surrounding lines use %llu for 64 bit numbers, so I'm assuming %lu is correct for 32bit, at least for the gcc they compiled with. Removing the line, since it is only user output, causes the program to hang on load and not show any output at all. I also tried compiling with -fno-builtin-fprintf thinking maybe my gcc was radically different than theirs and was doing something funky, and it did compile w/o errors, however it went back to not showing any output.

I have fetched the source from muliple sites in order to check the consistancy of this line and every version has it exactly as shown, so I'm thinking that the gcc ubuntu 9.04 ships with might not be a similar enough fork to the one used by the dev of this code. 

Any Thoughts?

---

### Post by wbryan6 on 2010-04-20
Bump.  I'm having the same problem.  I'm following and installation guide online that instructed me to run:```
gcc -02 vfdecrypt.c -o vfdecrypt -lcrypto
```

When I do, I get the same error output:
```
gcc: unrecognized option '-02'
vfdecrypt.c: In function ‘dump_v2_header’:
vfdecrypt.c:133: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 3 has type ‘uint32_t’
vfdecrypt.c:134: warning: format ‘%llu’ expects type ‘long long unsigned int’, but argument 3 has type ‘uint64_t’
vfdecrypt.c:135: warning: format ‘%llu’ expects type ‘long long unsigned int’, but argument 3 has type ‘uint64_t’

```

The 'unrecognized option' message on the first line could be user error, but I don't get a different result if I change it to 'O2'.  I'm also running Karmic AMD64.

---

### Post by HuckBerry on 2010-04-27
Ultimately, I think I found a pre-compiled copy of vfdecrypt somewhere because I couldn't find any documentation on which formatter was needed for that size variable. The lack of documentation was rather upsetting and the author of that work no longer seems to be actively developing it.

---

