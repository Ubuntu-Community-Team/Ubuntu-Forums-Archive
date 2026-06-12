---
title: "Possible bug on command 'find'."
date: 2011-09-24
forum: General Help
---

### Post by papibe on 2011-09-24
It looks like using **-execdir {} ;** or **-execdir {} +** makes no difference.

Example:
```
$ find  -name '*.o'
./all_devproj/qvdpautest-0.5.1/mainwidget.o
./all_devproj/qvdpautest-0.5.1/moc_vdpauwidget.o
./all_devproj/qvdpautest-0.5.1/mpeg4decoder.o
./all_devproj/qvdpautest-0.5.1/moc_mainwidget.o
./all_devproj/qvdpautest-0.5.1/main.o
./all_devproj/qvdpautest-0.5.1/mpegdecoder.o
./devproj/qvdpautest-0.5.1/vc1decoder.o
./devproj/qvdpautest-0.5.1/h264decoder.o
./devproj/qvdpautest-0.5.1/vdpaucontext.o
./devproj/qvdpautest-0.5.1/vdpauwidget.o

```
Now using the "execdir {} ;" option:
```
$ find  -name '*.o' -execdir bash -c 'echo $@' _ '{}' \;
./mainwidget.o
./moc_vdpauwidget.o
./mpeg4decoder.o
./moc_mainwidget.o
./main.o
./mpegdecoder.o
./vc1decoder.o
./h264decoder.o
./vdpaucontext.o
./vdpauwidget.o
```
So far so good, now the paths are relative to the directory.

But if I use the + option:
```
$ find  -name '*.o' -execdir bash -c 'echo $@' _ '{}' +
./mainwidget.o
./moc_vdpauwidget.o
./mpeg4decoder.o
./moc_mainwidget.o
./main.o
./mpegdecoder.o
./vc1decoder.o
./h264decoder.o
./vdpaucontext.o
./vdpauwidget.o
```
There's the trouble: results shouldn't be the same. If I understand correctly the man page, it should display one line per directory with every filename matched in that directory. Something like this:
```
$ find  -name '*.o' -execdir bash -c 'echo $@' _ '{}' +
./mainwidget.o ./moc_vdpauwidget.o ./mpeg4decoder.o ./moc_mainwidget.o ./main.o ./mpegdecoder.o
./vc1decoder.o ./h264decoder.o ./vdpaucontext.o ./vdpauwidget.o
```
Is that a bug?
Am I misunderstanding something?

I would appreciate any comments, hits, corrections, etc.
Regargs.

---

### Post by sisco311 on 2011-09-24
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=489046](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=489046)

---

### Post by papibe on 2011-09-24
I'm going to resume what I read on that link:
[LIST]
[*]Bug originally reported on July 2008.
[*]There's acknowledge that the output is restricted to one argument because of performance issues.
[*]Declaration that the bug is fixed on May 2010 (for version 4.5.9-1)
[/LIST]
Interestingly, although we pass from bash 4.1.5(1) (Lucid) to bash 4.2.8(1) (Natty), we are still stuck with findutils 4.4.2

And so far, [Oneiric]("http://packages.ubuntu.com/search?suite=oneiric&searchon=names&keywords=find%20utils") won't upgrade findutils.

:(

Regards.

---

