---
title: "Uggly fonts in an anpplication"
date: 2010-06-13
forum: General Help
---

### Post by fred6633 on 2010-06-13
Hello,

I have an application, which partly has ugly aliased fonts. It also takes time to load.

I get this output when I launch it:

./HansaWorld & 
[1] 1649
[email]fredrik@fredrik-desktop:~/.progra[/email]m/hansaworld-linux-5.4-client$ 2010-06-13 09:53:07 locale: sv_SE.utf8
2010-06-13 09:53:08 locale of fontset: sv_SE.utf8
2010-06-13 09:53:08 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso8859-1
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:08 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:08 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:08 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
2010-06-13 09:53:08 locale of fontset: sv_SE.utf8
2010-06-13 09:53:08 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso8859-1
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:08 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:08 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:08 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:08 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
2010-06-13 09:53:09 locale of fontset: sv_SE.utf8
2010-06-13 09:53:09 -b&h-lucida-bold-r-normal-sans-10-100-75-75-p-66-iso8859-1
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:09 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:09 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:09 -b&h-lucida-bold-r-normal-sans-10-100-75-75-p-66-iso10646-1
2010-06-13 09:53:09 locale of fontset: sv_SE.utf8
2010-06-13 09:53:09 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso8859-1
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:09 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:09 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:09 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:09 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
2010-06-13 09:53:10 locale of fontset: sv_SE.utf8
2010-06-13 09:53:10 -adobe-times-medium-r-normal--10-100-75-75-p-54-iso8859-1
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:10 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:10 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:10 -adobe-times-medium-r-normal--10-100-75-75-p-54-iso10646-1
2010-06-13 09:53:10 locale of fontset: sv_SE.utf8
2010-06-13 09:53:10 -adobe-times-bold-r-normal--10-100-75-75-p-57-iso8859-1
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:10 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:10 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:10 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:10 -adobe-times-bold-r-normal--10-100-75-75-p-57-iso10646-1
2010-06-13 09:53:11 locale of fontset: sv_SE.utf8
2010-06-13 09:53:11 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-1
2010-06-13 09:53:11 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-2
2010-06-13 09:53:11 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-4
2010-06-13 09:53:11 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:11 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-9
2010-06-13 09:53:11 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-14
2010-06-13 09:53:11 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:11 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:11 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso10646-1
2010-06-13 09:53:11 HansaWorld 5.4 (28) for Linux, (32-bit pointers, 64-bit db access) starting
2010-06-13 09:53:12 locale of fontset: sv_SE.utf8
2010-06-13 09:53:12 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso8859-1
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:12 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:12 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:12 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
2010-06-13 09:53:12 locale of fontset: sv_SE.utf8
2010-06-13 09:53:12 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso8859-1
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:12 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:12 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:12 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:12 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
2010-06-13 09:53:13 locale of fontset: sv_SE.utf8
2010-06-13 09:53:13 -b&h-lucida-bold-r-normal-sans-10-100-75-75-p-66-iso8859-1
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:13 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:13 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:13 -b&h-lucida-bold-r-normal-sans-10-100-75-75-p-66-iso10646-1
2010-06-13 09:53:13 locale of fontset: sv_SE.utf8
2010-06-13 09:53:13 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso8859-1
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:13 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:13 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:13 -b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
2010-06-13 09:53:13 locale of fontset: sv_SE.utf8
2010-06-13 09:53:13 -adobe-times-medium-r-normal--10-100-75-75-p-54-iso8859-1
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:13 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:13 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:13 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:13 -adobe-times-medium-r-normal--10-100-75-75-p-54-iso10646-1
2010-06-13 09:53:14 locale of fontset: sv_SE.utf8
2010-06-13 09:53:14 -adobe-times-bold-r-normal--10-100-75-75-p-57-iso8859-1
2010-06-13 09:53:14 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-2
2010-06-13 09:53:14 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-4
2010-06-13 09:53:14 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:14 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-9
2010-06-13 09:53:14 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-14
2010-06-13 09:53:14 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:14 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:14 -adobe-times-bold-r-normal--10-100-75-75-p-57-iso10646-1
2010-06-13 09:53:15 locale of fontset: sv_SE.utf8
2010-06-13 09:53:15 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-1
2010-06-13 09:53:15 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-2
2010-06-13 09:53:15 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-4
2010-06-13 09:53:15 -misc-fixed-medium-r-normal--10-100-75-75-c-60-koi8-r
2010-06-13 09:53:15 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-9
2010-06-13 09:53:15 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso8859-14
2010-06-13 09:53:15 -jis-fixed-medium-r-normal--10-72-100-100-c-0-jisx0208.1983-0
2010-06-13 09:53:15 -isas-fangsong ti-medium-r-normal--10-72-100-100-c-0-gb2312.1980-0
2010-06-13 09:53:15 -misc-fixed-bold-r-normal--10-72-100-100-c-0-iso10646-1
2010-06-13 09:53:15 iconv codeset: UTF-8

Does anyone know how to get good looking fonts? I remember when I tested FreeBSD a while ago that the same application looked good and started normally fast, so there must be a solution.

Thanks

Fred

---

### Post by an0dos on 2010-06-13
Do you have the "ubuntu restricted extras" package installed? You may need ms fonts. Does this program run in Wine? If so, you may need to install the "allfonts" package via winetricks.

---

### Post by fred6633 on 2010-06-13
Thanks, I have "ubuntu restricted extras" package installed. I've also added Vista's cleartype fonts, Calibri etc, so I don't think I lack fonts.

This is the linux version of the the program. I also have a Windows version. But I haven't tested it in Wine. I don't have Wine installed. But to me it's two different things how the linux version works in Ubuntu and how the Windows version works in wine.

Fred

---

