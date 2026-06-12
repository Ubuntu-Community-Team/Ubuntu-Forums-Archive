---
title: "Trouble with libcurl"
date: 2010-05-17
forum: General Help
---

### Post by epic93 on 2010-05-17
I installed and set up libcurl with apt-get install, and I downloaded a code sample from the libcurl website, but when I try to compile it, I get the error message 

> 
simple.c:(.text+0x99): undefined reference to `curl_easy_init'
simple.c:(.text+0xc6): undefined reference to `curl_easy_setopt'
simple.c:(.text+0xd2): undefined reference to `curl_easy_perform'
simple.c:(.text+0xe1): undefined reference to `curl_easy_cleanup'
collect2: ld returned 1 exit status



The source code that I am trying to compile is

> #include <stdio.h>
#include <curl/curl.h>
 
int main(void)
{
  CURL *curl;
  CURLcode res;
 
  curl = curl_easy_init();
  if(curl) {
    curl_easy_setopt(curl, CURLOPT_URL, "curl.haxx.se");
    res = curl_easy_perform(curl);
 
    /* always cleanup */ 
    curl_easy_cleanup(curl);
  }
  return 0;
}


---

### Post by marshmallow1304 on 2010-05-17
Did you link correctly?  adding -lcurl should do it.  Or using pkg-config, we have

```
g++ -o curl curl.cc `pkg-config --libs --cflags libcurl`
```

---

### Post by epic93 on 2010-05-17
> **marshmallow1304 said:**
> Did you link correctly?  adding -lcurl should do it.  Or using pkg-config, we have

```
g++ -o curl curl.cc `pkg-config --libs --cflags libcurl`
```

adding -lcurl did it. Thanks. (Still a bit new to programming I am.)

---

### Post by night_fox on 2010-11-27
This is silly. The same thing happened to me, and adding -lcurl solved it even though....

```
$ curl-config --libs
-lcurl -Wl,-Bsymbolic-functions
```

.... it gets included by curl-config!

---

### Post by night_fox on 2010-11-27
damn, silly me, I had cflags and libs the wrong way round in my Makefile

---

