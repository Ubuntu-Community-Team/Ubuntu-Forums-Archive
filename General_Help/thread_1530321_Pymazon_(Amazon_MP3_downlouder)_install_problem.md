---
title: "Pymazon (Amazon MP3 downlouder) install problem"
date: 2010-07-13
forum: General Help
---

### Post by Bryan55 on 2010-07-13
Hi
First of all you will have to realize that when it comes to command lines I am a novice.

I have tried to install Pymazon twice. The first time following the instructions from here. 

_[http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/)_

There was a lot of trial and error on my part and I can add all the terminal entries if that will help. (How do you enter it into one of those scrollable field on this forum?) 
Here is what I got when I tried to open Pymazon.
> bryan@Bydand:~/Pymazon-0.9$ pymazon
Traceback (most recent call last):
  File "/usr/local/bin/pymazon", line 67, in <module>
    main()
  File "/usr/local/bin/pymazon", line 41, in main
    main(amzs)
  File "/usr/local/lib/python2.6/dist-packages/pymazon/qt/ui.py", line 259, in main
    win = MainWindow(amzs)
  File "/usr/local/lib/python2.6/dist-packages/pymazon/qt/ui.py", line 118, in __init__
    loadFileIcon = QIcon.fromTheme('document-new', QIcon(QPixmap(load_icon_path)))
AttributeError: type object 'QIcon' has no attribute 'fromTheme'This output means very little to me and my first instinct was that I should remove what I had done and start again unfortunately i don't know how to.

The second go at installing it I followed the instructions from here.

_[http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html](http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html)_

This time it went very smoothly and I felt I had done it but when I try to open Pymazon I get.
> bryan@Bydand:~$ pymazon &#8211;g
Traceback (most recent call last):
  File "/usr/local/bin/pymazon", line 67, in <module>
    main()
  File "/usr/local/bin/pymazon", line 32, in main
    entry, amzs = parse_options()   
  File "/usr/local/lib/python2.6/dist-packages/pymazon/core/options.py", line 101, in parse_options
    amzs = validate_args(args)
  File "/usr/local/lib/python2.6/dist-packages/pymazon/core/options.py", line 29, in validate_args
    raise ValueError('Positional arguments must be .amz files.')        
ValueError: Positional arguments must be .amz files.Any help would be very welcome.

Bryan.

edit .. Something has just occurred to me. Do I have to have downloaded a MP3 before the Pymason GUI will open?

---

### Post by sccolbert on 2010-07-13
> **Bryan55 said:**
> Hi
First of all you will have to realize that when it comes to command lines I am a novice.

I have tried to install Pymazon twice. The first time following the instructions from here. 

_[http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/)_

There was a lot of trial and error on my part and I can add all the terminal entries if that will help. (How do you enter it into one of those scrollable field on this forum?) 
Here is what I got when I tried to open Pymazon.
This output means very little to me and my first instinct was that I should remove what I had done and start again unfortunately i don't know how to.

The second go at installing it I followed the instructions from here.

_[http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html](http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html)_

This time it went very smoothly and I felt I had done it but when I try to open Pymazon I get.
Any help would be very welcome.

Bryan.

edit .. Something has just occurred to me. Do I have to have downloaded a MP3 before the Pymason GUI will open?


Hi, I am the author of Pymazon. 

The first error is a Qt related error. It looks like you have an old version of Qt. You need at least Qt 4.6. What version of Ubuntu are you using? 

For the second error. Don't follow the instructions on that site, it's for an old version of Pymazon. Use the instructions on the Pymazon site (the Google code site). For now, just try using the gtk backend with the following command:

$ pymazon -g gtk 

Hopefully that won't give you errors, but if you are on a really old version, it may. 

No, you do not need to have an mp3 downloaded to run the Pymazon gui. 


Cheers!

Chris

---

### Post by Bryan55 on 2010-07-14
Hi sccolbert.

sscolbert wrote
> The first error is a Qt related error. It looks like you have an old version of Qt. You need at least Qt 4.6. What version of Ubuntu are you using?I'm using 9.10 installed using the Alternate disc.

> $ pymazon -g gtkThis worked. GUI opened but I got a warning.
> bryan@Bydand:~$ pymazon -g gtk 
Warning:
Unknown property: GtkAction.always-show-image
Warning:
GtkSpinButton: setting an adjustment with non-zero page size is deprecated


Do I need to do any more? I want to make sure I don't get any problems.

Thanks for the help.

Bryan.

---

### Post by sccolbert on 2010-07-14
> **Bryan55 said:**
> Hi sccolbert.

sscolbert wrote
I'm using 9.10 installed using the Alternate disc.

This worked. GUI opened but I got a warning.



Do I need to do any more? I want to make sure I don't get any problems.

Thanks for the help.

Bryan.


Ah, ok. 9.10 uses Qt 4.5 which explains the Qt error. I didn't realize the QIcon.fromtheme(...) feature was such a recent Qt addition. I will fix that in the 1.0 release of Pymazon so that it doesn't cause that error. 


As far as the warnings, you can ignore them. It's just gtk complaining, which happens all the time.

---

### Post by Bryan55 on 2010-07-15
OK Chris I will keep an eye out for the new release.

Thanks for you help and keep up the good work.

Bryan.

---

