---
title: "Strange headers from my ip address in Apache error and access logs"
date: 2011-05-10
forum: General Help
---

### Post by louieaw on 2011-05-10
[FONT=Arial]So I was looking at my Apache access log, and I noticed something strange (aside from the ordinary brute force attempts... )

[/FONT]```
[FONT=Arial]174.129.117.237 - - [10/May/2011:06:28:09 -0400] "HEAD / HTTP/1.1" 302 232 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.13 (KHTML, like Gecko) Chrome/0.A.B.C Safari/525.13"
163.27.210.71 - - [10/May/2011:06:32:13 -0400] "GET /w00tw00t.at.blackhats.romanian.anti-sec:) HTTP/1.1" 404 415 "-" "ZmEu"
163.27.210.71 - - [10/May/2011:06:32:14 -0400] "GET /phpMyAdmin/scripts/setup.php HTTP/1.1" 404 405 "-" "ZmEu"
MY IP - - [10/May/2011:07:29:10 -0400] "]H\xd5\xa9)<\xde\x99b\xc1Z\xc1>R\xf5\xf9z\\P\xbb\xaa``\xeaqk(\xc3\x84\xd1V\x9f\xd5pt\x95;gJ\xd6" 302 176 "-" "-"
MY IP - - [10/May/2011:07:33:08 -0400] "\xaeZzJ\xb4j\xf8\xca\xf7b\x13\xe4\xa7" 302 176 "-" "-"
MY IP - - [10/May/2011:07:36:09 -0400] "s\x80\v\xd2\x7f!'\xe7N\x06\xf7M" 400 226 "-" "-"
MY IP - - [10/May/2011:07:40:12 -0400] "\x86\xae" 302 176 "-" "-"
MY IP - - [10/May/2011:07:42:20 -0400] "\x90]e\x12\xb8P\v\xadW\xe8\xcd\xb2]\xf3\x9c\x88" 400 226 "-" "-"
MY IP - - [10/May/2011:07:45:08 -0400] "d\xacF" 302 176 "-" "-"
MY IP - - [10/May/2011:07:59:09 -0400] "\x93\xe4Ip\xad\xa9\xdd?>\xee\x85\xacC" 302 176 "-" "-"
MY IP - - [10/May/2011:08:17:26 -0400] "F \x98\xcc\x0f\xb9#" 400 226 "-" "-"
MY IP - - [10/May/2011:08:17:26 -0400] "\x98\xe3" 302 176 "-" "-"
MY IP - - [10/May/2011:08:29:09 -0400] "U\x1f\xdc8\xae\xd0\xff\xcd\x82F\xc7\x87\xfe\x1d\x90\x9a`\t\xe7\x15\xdc\x97\xbfl\xeb\xbc\x84LZ\xc0$\xda/\x8d\xbd\x93_\xd4" 400 226 "-" "-"
MY IP - - [10/May/2011:09:31:10 -0400] "^\xab\xe2\x85\x1a\x94\xc4d^\xf9\x97)\x14\xff\x06et\x05@\x8f+\xd4\x1e\x834" 302 176 "-" "-"
MY IP - - [10/May/2011:09:38:10 -0400] "\xa1\xe9\"d\xdd\xe0yb\x90\xb8\xf1\xbe\x8fidfB\xd2\xf1\xa7\x86\x02rl\x15\x1c\x8f" 302 176 "-" "-"
MY IP - - [10/May/2011:10:13:09 -0400] "\xa3\x9a\x96`J\xd2\x8e/N@\xe7\x84\xfb+\xa0\x80iC\xa3{\x04\xbc\xb2\xc2\xd8\xd7\xd3\xe3\x99" 302 176 "-" "-"
MY IP - - [10/May/2011:10:14:11 -0400] "\x1cS=\xf0\xf20\xfa\xd6\xb3\x19" 302 176 "-" "-"
MY IP - - [10/May/2011:10:22:11 -0400] "\xf4a\xc3\xaf\xcb\xa9x\x10]\x9e'l5\xdf$>\xda;\xbdN\xe9\v\xd9\xbd\xde\x14" 400 226 "-" "-"
MY IP - - [10/May/2011:10:26:11 -0400] "\xa1\xfc\xb4o\x9b:Z\xa5\xe6\xf3wD~_\xf6m8NFc\xf9c\xd2}Z\xa2\x9d\xb9\xcb\\\x19\xa5[\t\xd7Tk\x14\xf32\xa0*\r}\xbc\xcb\x18\x1b*c\xd6)" 400 415 "-" "-"
MY IP - - [10/May/2011:10:48:11 -0400] "\xb6\xce@\vODs\xab\x02e\xcb\xa9O\xd4.\x07]\xecN)\xd1\xeaWr\xdf\x96\xb5\xc6\xb6\xfb\xbeg6\x87o\x16@\x8f\x97`\xd3\xdc\x8a" 400 226 "-" "-"
MY IP - - [10/May/2011:11:13:14 -0400] "\x04h\xc7\xec\x98\x14\xfa\xab\x073\x15\xf2\xf2{\xffz\x99\x13\xceT" 302 176 "-" "-"
46.4.95.200 - - [10/May/2011:11:14:02 -0400] "GET / HTTP/1.1" 302 404 "http://dom-v-anape.ru/" "Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/534.1 (KHTML, like Gecko) Chrome/6.0.427.0 Safari/534.1"
46.4.95.200 - - [10/May/2011:11:14:05 -0400] "GET / HTTP/1.1" 302 404 "-" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)"
MY IP - - [10/May/2011:11:45:11 -0400] "\x18E\x83?\"\xfb\xf4\xf0\xf4B=(r\x02\x81\x1c\x86K\xc4\xa2\xa3\xdfNp<!\x8f\x1c\t\x86\xbd\xd5\xfc" 400 226 "-" "-"
MY IP - - [10/May/2011:11:46:14 -0400] "J\x03\x98P\x8b\xf3e\x11\xe7\xb7f@@r\xe4q\xf2M\xfa\x1c\xf5h9+>~C\xb1\xa7\xc9\xbdaD\x8e\xb8fZ\xfe\xeb\x03\x88\x13d\x820\xed\xf3l\xdf\x9ef\xddY\x80\xe0\xc8\xd6\xa1\xdf" 302 176 "-" "-"
MY IP - - [10/May/2011:11:56:11 -0400] "\xbf\b\x82d\x9f\xf2\xa1" 302 176 "-" "-"
MY IP - - [10/May/2011:12:04:10 -0400] "O\x8f;\x1fC~\x0fg;\xcc\xd7" 302 176 "-" "-"
MY IP - - [10/May/2011:12:13:11 -0400] "\xb6\x1e\xd8\x12\xfe\x9f\xc0\xb3\xb7\x9b\xf0\xa13\xad\x97G\xc1\x8d\xa0Fm\x8b " 302 176 "-" "-"
MY IP - - [10/May/2011:12:29:11 -0400] "\xfc\xc5\x1dq\x95\xabf\xdd\xc5\xa6\x96\x15\xad\xdc" 302 176 "-" "-"
MY IP - - [10/May/2011:12:45:11 -0400] "\x12\x93@\xac\xb4\xd1!\xf4e\x93\xe3\xe3\x87\xde\x13\xff\x02\x8c\xec\xb4<\xe7\"C\xffM\xd2" 302 176 "-" "-"
[/FONT]
```[FONT=Arial]

And I was wondering what exactly is going on. And what all that "/x" hex stuff is. Any ideas/help would be appreciated!

Obviously, "MY IP" is my ip address, which I don't really want to share...

Linux Mint 10 AMD64
[/FONT]

---

