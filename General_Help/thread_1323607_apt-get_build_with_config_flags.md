---
title: "apt-get build with config flags"
date: 2009-11-11
forum: General Help
---

### Post by bnut on 2009-11-11
I'm building a dedicated MediaTomb server and I'm running into some issues.

Using the version from Synaptic (or apt-get install) results in some segfaults.  Doing a bit of research, I find that if I can build it without taglib I can avoid the segfaults (due to mkv imports into the db or something like that).  You can see the comments in [this blog post]("http://blog.flexion.org/index.php/2009/02/07/mediatomb-012-streaming-audio-and-video-around-the-house/") for specific details.

```
Nov  9 21:33:40 mediaserver kernel: [ 9606.770349] mediatomb[3214]: segfault at a249fab ip 00cdf01a sp b354c61c error 6 in libc-2.10.1.so[c6a000+13e000]
Nov  9 21:56:49 mediaserver kernel: [10995.253799] mediatomb[3398]: segfault at 8 ip 009a5448 sp b13ff10c error 6 in libc-2.10.1.so[938000+13e000]

```I've been working through the manual steps.  Retrieve the source, configure with the --disable-taglib, resolve dependencies, etc.  But during the Make I'm running into an error I can't quite figure out:

```
make[2]: Entering directory `/home/bryan/source/mediatomb-0.12.0~svn2018/build&apos;
g++ -DHAVE_CONFIG_H -I. -I.. -I../tombupnp/upnp/inc    -I../src -I../tombupnp/ixml/inc -I../tombupnp/threadutil/inc -I../tombupnp/upnp/inc -I..  -I/usr/include/mysql  -DBIG_JOINS=1  -fno-strict-aliasing   -DUNIV_LINUX         -pthread        -g -O2 -MT libmediatomb_a-tools.o -MD -MP -MF .deps/libmediatomb_a-tools.Tpo -c -o libmediatomb_a-tools.o `test -f &apos;../src/tools.cc&apos; || echo &apos;./&apos;`../src/tools.cc
../src/tools.cc: In function ‘zmm::String hex_decode_string(zmm::String)’:
../src/tools.cc:306: error: invalid conversion from ‘const char*’ to ‘char*’
../src/tools.cc:307: error: invalid conversion from ‘const char*’ to ‘char*’
../src/tools.cc: In function ‘zmm::String url_unescape(zmm::String)’:
../src/tools.cc:402: error: invalid conversion from ‘const char*’ to ‘char*’
../src/tools.cc:408: error: invalid conversion from ‘const char*’ to ‘char*’
make[2]: *** [libmediatomb_a-tools.o] Error 1
make[2]: Leaving directory `/home/bryan/source/mediatomb-0.12.0~svn2018/build&apos;
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/source/mediatomb-0.12.0~svn2018&apos;
make: *** [all] Error 2

```I'm not a code jockey, so I don't know where/what to comment out to get past this.  But, I'm wondering... _* is there a way to install from apt-get with config switches?*_

Is there an alternate solution?  If I de-install taglib (I already did) can I get the binary to install without that dependency (such as a manual deselection)?  OR, can someone advise me how to move past the error I'm getting in the make.


Hopefully, I'm posting this in the right section.  My reasoning is that it's not really a multimedia specific issue as much as it is a question about apt-get.

Thanks in advance.

---

