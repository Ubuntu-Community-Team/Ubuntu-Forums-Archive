---
title: "g++ compiler errors with vector class after installing/uninstalling libstlport"
date: 2009-09-16
forum: General Help
---

### Post by Gatemaze on 2009-09-16
Hello,

I am trying to run the following simple program:

```

#include <vector>

int main()
{
return 0;
}

```

and I am getting a bunch of errors (see later below). This compiled fine initially and it start giving me these errors after I installed (and then uninstalled) libstlport from the repos.It also compiles fine on other machines with the "initial" packages and without ever installing/uninstalling libstlport. Any help? Many thanks.

The "tail" of the errors are:

```

./vector:180: error: stray &#8216;\223&#8217; in program
./vector:180:35: warning: null character(s) ignored
./vector:180: error: stray &#8216;\256&#8217; in program
./vector:180:43: warning: null character(s) ignored
./vector:180: error: stray &#8216;\22&#8217; in program
./vector:180:47: warning: null character(s) ignored
./vector:180: error: stray &#8216;\365&#8217; in program
./vector:180:59: warning: null character(s) ignored
./vector:180: error: stray &#8216;\306&#8217; in program
./vector:180:67: warning: null character(s) ignored
./vector:180:70: warning: null character(s) preserved in literal
./vector:180:70: warning: missing terminating " character
./vector:180: error: missing terminating " character
./vector:181:1: warning: null character(s) ignored
./vector:181:2: warning: null character(s) preserved in literal
./vector:181:23: warning: null character(s) ignored
./vector:182:1: warning: null character(s) ignored
./vector:182: error: stray &#8216;\304&#8217; in program
./vector:182: error: stray &#8216;\25&#8217; in program
./vector:182: error: stray &#8216;@&#8217; in program
./vector:182:5: warning: null character(s) ignored
./vector:182:11: warning: null character(s) ignored
./vector:182:22: warning: null character(s) preserved in literal
./vector:182:22: warning: missing terminating " character
./vector:182: error: missing terminating " character
./vector:183:1: warning: null character(s) ignored
./vector:183: error: stray &#8216;\216&#8217; in program
./vector:183: error: stray &#8216;\22&#8217; in program
./vector:183: error: stray &#8216;@&#8217; in program
./vector:183:5: warning: null character(s) ignored
./vector:183:11: warning: null character(s) ignored
./vector:183:19: warning: null character(s) ignored
./vector:183:22: warning: null character(s) preserved in literal
./vector:183:22: warning: missing terminating " character
./vector:183: error: missing terminating " character
./vector:184:1: warning: null character(s) ignored
./vector:185: error: stray &#8216;@&#8217; in program
./vector:185:2: warning: null character(s) ignored
./vector:185:8: warning: null character(s) ignored
./vector:185: error: stray &#8216;\201&#8217; in program
./vector:185:16: warning: null character(s) ignored
./vector:185:19: warning: null character(s) preserved in literal
./vector:185:19: warning: missing terminating " character
./vector:185: error: missing terminating " character
./vector:186:1: warning: null character(s) ignored
./vector:186: error: stray &#8216;\234&#8217; in program
./vector:186: error: stray &#8216;\20&#8217; in program
./vector:186: error: stray &#8216;@&#8217; in program
./vector:186:5: warning: null character(s) ignored
./vector:186:11: warning: null character(s) ignored
./vector:186: error: stray &#8216;\235&#8217; in program
./vector:186:19: warning: null character(s) ignored
./vector:186:22: warning: null character(s) preserved in literal
./vector:186:22: warning: missing terminating " character
./vector:186: error: missing terminating " character
./vector:187:1: warning: null character(s) ignored
./vector:187: error: stray &#8216;\230&#8217; in program
./vector:187: error: stray &#8216;\16&#8217; in program
./vector:187: error: stray &#8216;@&#8217; in program
./vector:187:5: warning: null character(s) ignored
./vector:187: error: stray &#8216;\36&#8217; in program
./vector:187:11: warning: null character(s) ignored
./vector:187: error: stray &#8216;\272&#8217; in program
./vector:187:19: warning: null character(s) ignored
./vector:187: error: stray &#8216;\22&#8217; in program
./vector:187:23: warning: null character(s) ignored
./vector:188:1: warning: null character(s) ignored
./vector:188: error: stray &#8216;\30&#8217; in program
./vector:188: error: stray &#8216;\10&#8217; in program
./vector:188: error: stray &#8216;@&#8217; in program
./vector:188:5: warning: null character(s) ignored
./vector:188: error: stray &#8216;\2&#8217; in program
./vector:188:12: warning: null character(s) ignored
./vector:188: error: stray &#8216;\277&#8217; in program
./vector:188:19: warning: null character(s) ignored
./vector:188: error: stray &#8216;\22&#8217; in program
./vector:188:23: warning: null character(s) ignored
./vector:188: error: stray &#8216;\220&#8217; in program
./vector:188: error: stray &#8216;\6&#8217; in program
./vector:188: error: stray &#8216;@&#8217; in program
./vector:188:29: warning: null character(s) ignored
./vector:188: error: stray &#8216;\305&#8217; in program
./vector:188:43: warning: null character(s) ignored
./vector:188:46: warning: null character(s) preserved in literal
./vector:188:46: warning: missing terminating " character
./vector:188: error: missing terminating " character
./vector:189:1: warning: null character(s) ignored
./vector:189: error: stray &#8216;\340&#8217; in program
./vector:190: error: stray &#8216;@&#8217; in program
./vector:190:2: warning: null character(s) ignored
./vector:191:1: warning: null character(s) ignored
./vector:191: error: stray &#8216;\351&#8217; in program
./vector:191:9: warning: null character(s) ignored
./vector:191:12: warning: null character(s) preserved in literal
./vector:191:12: warning: missing terminating " character
./vector:191: error: missing terminating " character
./vector:192:1: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:2: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:8: warning: null character(s) ignored
./vector:193:22: warning: null character(s) ignored
./vector:193:33: warning: null character(s) ignored
./vector:193:49: warning: null character(s) ignored
./vector:193:60: warning: null character(s) ignored
./vector:193:74: warning: null character(s) ignored
./vector:193:88: warning: null character(s) ignored
./vector:193:101: warning: null character(s) ignored
./vector:193:123: warning: null character(s) ignored
./vector:193:138: warning: null character(s) ignored
./vector:193:145: warning: null character(s) ignored
./vector:193:157: warning: null character(s) ignored
./vector:193:170: warning: null character(s) ignored
./vector:193:183: warning: null character(s) ignored
./vector:193:197: warning: null character(s) ignored
./vector:193:209: warning: null character(s) ignored
./vector:193:231: warning: null character(s) ignored
./vector:193:247: warning: null character(s) ignored
./vector:193:269: warning: null character(s) ignored
./vector:193:286: warning: null character(s) ignored
./vector:193:305: warning: null character(s) ignored
./vector:193:314: warning: null character(s) ignored
./vector:193:325: warning: null character(s) ignored
./vector:193:361: warning: null character(s) ignored
./vector:193:409: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:452: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:468: error: too many decimal points in number
./vector:193:472: warning: null character(s) ignored
./vector:193:527: warning: null character(s) ignored
./vector:193:636: warning: null character(s) ignored
./vector:193:652: warning: null character(s) ignored
./vector:193:659: warning: null character(s) ignored
./vector:193:729: warning: null character(s) ignored
./vector:193:793: warning: null character(s) ignored
./vector:193:859: warning: null character(s) ignored
./vector:193:891: warning: null character(s) ignored
./vector:193:965: warning: null character(s) ignored
./vector:193:994: warning: null character(s) ignored
./vector:193:1009: warning: null character(s) ignored
./vector:193:1029: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:1049: warning: null character(s) ignored
./vector:193:1065: warning: null character(s) ignored
./vector:193:1092: warning: null character(s) ignored
./vector:193:1098: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:1115: error: too many decimal points in number
./vector:193:1119: warning: null character(s) ignored
./vector:193:1181: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:1208: error: too many decimal points in number
./vector:193:1212: warning: null character(s) ignored
./vector:193:1248: warning: null character(s) ignored
./vector:193:1298: warning: null character(s) ignored
./vector:193:1306: warning: null character(s) ignored
./vector:193:1365: warning: null character(s) ignored
./vector:193:1443: warning: null character(s) ignored
./vector:193:1468: warning: null character(s) ignored
./vector:193:1501: warning: null character(s) ignored
./vector:193:1548: warning: null character(s) ignored
./vector:193:1563: warning: null character(s) ignored
./vector:193:1614: warning: null character(s) ignored
./vector:193:1627: warning: null character(s) ignored
./vector:193:1698: warning: null character(s) ignored
./vector:193:1741: warning: null character(s) ignored
./vector:193:1770: warning: null character(s) ignored
./vector:193:1805: warning: null character(s) ignored
./vector:193:1829: warning: null character(s) ignored
./vector:193:1842: warning: null character(s) ignored
./vector:193:1904: warning: null character(s) ignored
./vector:193:1933: warning: null character(s) ignored
./vector:193:1973: warning: null character(s) ignored
./vector:193:2051: warning: null character(s) ignored
./vector:193:2067: warning: null character(s) ignored
./vector:193:2128: warning: null character(s) ignored
./vector:193:2141: warning: null character(s) ignored
./vector:193:2154: warning: null character(s) ignored
./vector:193:2199: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:2216: error: too many decimal points in number
./vector:193:2220: warning: null character(s) ignored
./vector:193:2261: warning: null character(s) ignored
./vector:193:2273: warning: null character(s) ignored
./vector:193:2289: warning: null character(s) ignored
./vector:193:2332: warning: null character(s) ignored
./vector:193:2376: warning: null character(s) ignored
./vector:193:2401: warning: null character(s) ignored
./vector:193:2439: warning: null character(s) ignored
./vector:193:2498: warning: null character(s) ignored
./vector:193:2503: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:2541: warning: null character(s) ignored
./vector:193:2593: warning: null character(s) ignored
./vector:193:2679: warning: null character(s) ignored
./vector:193:2725: warning: null character(s) ignored
./vector:193:2773: warning: null character(s) ignored
./vector:193:2780: warning: null character(s) ignored
./vector:193:2852: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:2885: warning: null character(s) ignored
./vector:193:2928: warning: null character(s) ignored
./vector:193:2941: warning: null character(s) ignored
./vector:193:2985: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:3004: warning: null character(s) ignored
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193: error: stray &#8216;@&#8217; in program
./vector:193:3028: warning: null character(s) ignored
./vector:193:3060: warning: null character(s) ignored
./vector:193:3095: warning: null character(s) ignored
./vector:193:3141: warning: null character(s) ignored
./vector:193:3215: warning: null character(s) ignored
./vector:193:3243: warning: null character(s) ignored
./vector:193:3272: warning: null character(s) ignored
./vector:193:3277: warning: null character(s) ignored
./vector:193:3283: warning: null character(s) ignored
./vector:193:3319: warning: null character(s) ignored
./vector:193:3412: warning: null character(s) ignored
./vector:193:3413: warning: no newline at end of file
./vector:1: error: expected constructor, destructor, or type conversion before &#8216;>&#8217; token
./vector:5: error: expected declaration before &#8216;}&#8217; token

```

---

### Post by mbarbier on 2010-11-08
A possible problem is this:

You might have an executable with the name "vector" in the path of the g++ preprocessor.
The g++ preprocessor includes this one (instead of the vector.h which you want him to include) in the program.

I had this problem when compiling a file which I called "vector.c":
The compiler runs the first time perfect. If you compile again he sees the file "vector" in the directory, so he does include this one, and this results in the error you mentionned.

Michael Barbier

---

