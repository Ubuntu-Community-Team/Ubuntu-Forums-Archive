---
title: "IRSSI and Character Encoding"
date: 2006-06-17
forum: General Help
---

### Post by Foucault on 2006-06-17
Hello everyone,
I've recently started using IRSSI for IRC, which seems very interesting, however there seems to be a problem in encoding and therefore I can not see any greek characters. My terminal supports greek characters (I can type greek and read filenames in greek). However in IRSSI all greek characters are shown as (?) -see attached screenshot- . I've tried changing the encoding to iso8859-7 (greek)  by issuing the command **/set term_charset iso8859-7** however the same problem persists. Is it IRSSI's problem or my terminal's? Any ideas (if any) to fix it?

In X-Chat I only need to change the encoding (character set option) in the server settings. However I don't really like X-Chat :P

Thanks everyone in advance!

---

### Post by jessicaNZ on 2006-10-07
I recently had a similar problem but I wanted to use UTF-8 (to see German characters). I found this website which helped me [http://jerakeen.org/blog/2005/06/23/screen-irssi-utf8/]("http://jerakeen.org/blog/2005/06/23/screen-irssi-utf8/") .

He suggests makeing sure that the 'LANG' environment variable is set. For you the command you have to run might be something like:
```
export LANG=el_GR.iso88597
```(but I'm not sure because I never use Greek encoding myself)

You would run that in your terminal (assuming you're using bash) before starting irssi.  If it works you can put that line in your ~/.bashrc file like so:
```
echo -e "#this sets my character encoding to Greek \nexport LANG=el_GR.iso88597" >>~/.bashrc
```Then you don't have to remember to run it every time because it will be run automaticly when you start bash.

good luck and have fun with irssi :)
- Jessica

---

