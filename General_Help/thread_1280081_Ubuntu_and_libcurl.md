---
title: "Ubuntu and libcurl"
date: 2009-10-01
forum: General Help
---

### Post by drgadget on 2009-10-01
Hi,

I'm trying to use libcurl ([http://curl.haxx.se](http://curl.haxx.se)) on Ubuntu 9.04. I've installed the following packages with synaptic:

curl
libcurl3
libcurl3-dbg
libcurl3-gnutls
libcurl4-openssl-dev

and I'm using Geany, but I'm still getting compiler errors, does anyone knows what to do?


I'm getting these compiler errors: 

```

gcc -Wall -o "simple" "simple.c" (in directory: /home/rogier/Desktop)
/tmp/ccc4X3Db.o: In function `main':
simple.c:(.text+0x8a): undefined reference to `curl_easy_init'
simple.c:(.text+0xb4): undefined reference to `curl_easy_setopt'
simple.c:(.text+0xbf): undefined reference to `curl_easy_perform'
simple.c:(.text+0xcd): undefined reference to `curl_easy_cleanup'
collect2: ld returned 1 exit status
Compilation failed.

```Anybody able to help me out?

Thanks in advance, 

Dr. Gadget

---

### Post by drgadget on 2009-10-02
I've installed Code::Blocks now. I still have the same packages (libcurl & curl etc.) and I've done some things with the compiler. First I've added to Settings > Compiler & Debugger > Search Directories > Compiler the value /usr/include/ and to Search Directories > Linker /usr/lib/ and to the linker itself: libcurl.a 

But now I'm getting other errors:

```

Compiling: /home/rogier/Desktop/simple.c
Linking console executable: /home/rogier/Desktop/simple
/usr/lib/libcurl.a(strerror.o): In function `Curl_idn_strerror':
(.text+0x2cb): undefined reference to `idna_strerror'
/usr/lib/libcurl.a(sslgen.o): In function `Curl_ssl_data_pending':
(.text+0x142): undefined reference to `SSL_pending'
/usr/lib/libcurl.a(timeval.o): In function `curlx_tvnow':
(.text+0x89): undefined reference to `clock_gettime'
/usr/lib/libcurl.a(url.o): In function `fix_hostname':
(.text+0x7fe): undefined reference to `stringprep_check_version'
/usr/lib/libcurl.a(url.o): In function `fix_hostname':
(.text+0x823): undefined reference to `idna_to_ascii_lz'
/usr/lib/libcurl.a(url.o): In function `fix_hostname':
(.text+0x82a): undefined reference to `stringprep_locale_charset'
/usr/lib/libcurl.a(url.o): In function `fix_hostname':
(.text+0x863): undefined reference to `idna_to_unicode_lzlz'
/usr/lib/libcurl.a(url.o): In function `fix_hostname':
(.text+0x8c8): undefined reference to `tld_check_lz'
/usr/lib/libcurl.a(url.o): In function `fix_hostname':
(.text+0x8dd): undefined reference to `idn_free'
/usr/lib/libcurl.a(url.o): In function `fix_hostname':
(.text+0x8ee): undefined reference to `tld_strerror'
/usr/lib/libcurl.a(url.o): In function `Curl_disconnect':
(.text+0xcbd): undefined reference to `idn_free'
/usr/lib/libcurl.a(url.o): In function `Curl_disconnect':
(.text+0xccc): undefined reference to `idn_free'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x8e): undefined reference to `ldap_url_parse'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0xa6): undefined reference to `ldap_err2string'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0xd7): undefined reference to `ldap_msgfree'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0xf0): undefined reference to `ldap_free_urldesc'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x102): undefined reference to `ldap_unbind_s'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x1b8): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x1d0): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x1e5): undefined reference to `ldap_init'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x21f): undefined reference to `ldap_simple_bind_s'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x263): undefined reference to `ldap_search_s'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x282): undefined reference to `ldap_first_entry'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x2ad): undefined reference to `ldap_get_dn'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x331): undefined reference to `ldap_first_attribute'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x355): undefined reference to `ldap_get_values_len'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x4f5): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x50d): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x580): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x5d5): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x5ed): undefined reference to `ldap_err2string'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x639): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x668): undefined reference to `ldap_simple_bind_s'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x686): undefined reference to `ldap_err2string'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x6e1): undefined reference to `ldap_err2string'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x721): undefined reference to `ldap_err2string'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x74f): undefined reference to `ldap_value_free_len'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x77d): undefined reference to `ldap_memfree'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x796): undefined reference to `ldap_next_attribute'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x7ac): undefined reference to `ldap_memfree'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x7c3): undefined reference to `ber_free'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x7d5): undefined reference to `ldap_next_entry'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x800): undefined reference to `ldap_init'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x827): undefined reference to `ldap_set_option'
/usr/lib/libcurl.a(ldap.o): In function `Curl_ldap':
(.text+0x83f): undefined reference to `ldap_err2string'
/usr/lib/libcurl.a(ssluse.o): In function `Curl_ossl_version':
(.text+0xc): undefined reference to `SSLeay'
/usr/lib/libcurl.a(ssluse.o): In function `Curl_ossl_recv':
(.text+0xf0): undefined reference to `SSL_read'
/usr/lib/libcurl.a(ssluse.o): In function `Curl_ossl_recv':
(.text+0x12e): undefined reference to `SSL_get_error'
/usr/lib/libcurl.a(ssluse.o): In function `Curl_ossl_recv':
(.text+0x161): undefined reference to `ERR_get_error'
/usr/lib/libcurl.a(ssluse.o): In function `Curl_ossl_recv':
(.text+0x181): undefined reference to `ERR_error_string'
Process terminated with status 1 (0 minutes, 2 seconds)
50 errors, 0 warnings
 
```

on this peace of script:
```

/*****************************************************************************
 *                                  _   _ ____  _
 *  Project                     ___| | | |  _ \| |
 *                             / __| | | | |_) | |
 *                            | (__| |_| |  _ <| |___
 *                             \___|\___/|_| \_\_____|
 *
 * $Id: simple.c,v 1.6 2004/08/23 14:22:52 bagder Exp $
 */

#include <stdio.h>
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

```

---

### Post by slayer_7in on 2010-01-06
Hi you can probably find the solution on the below mentioned link 

[http://curl.haxx.se/mail/lib-2005-04/0251.html](http://curl.haxx.se/mail/lib-2005-04/0251.html)

and this is what the link says 


This is a link error, and happens because you haven't told the linker to link  
with libcurl, or you didn't point out the proper dir for it to find it. 

  -lcurl 

or possibly 

  -L/path/to/dir/with/libcurl -lcurl 

... is probably what you need to add. :guitar:

---

