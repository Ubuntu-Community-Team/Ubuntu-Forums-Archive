---
title: "Disappointed - no OCR Scanning?"
date: 2010-05-08
forum: General Help
---

### Post by MetaMs on 2010-05-08
After installing Ubuntu on my laptop, which I generally use for simple tasks, I now have it on my desktop. Thinking that there were Windows alternatives to nearly everything, this morning I went looking for an alternative to ReadIRIS OCR software.

After spending several hours of wasted time I have learned that unless you're practically at the Linux developer level, OCR scanning apparently isn't possible in Ubuntu. I have to admit I'm pretty disillusioned since this is my first attempt to do an actual "job" on my new OS.

I'm posting this in the hope that someone will come up with a good GUI OCR package. If no one asks...no one will create it. Right?

For now, I guess I'm reduced to installing Wine, which I had hoped to avoid, given the reports of stuff not working properly.

If anyone does have any suggestions, I'd love to hear them.

---

### Post by TheNerdAL on 2010-05-08
This link might help: [https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

---

### Post by nalin4linux77 on 2010-05-23
Dear friends,easy-ocr 1.5 is released and we have made it more user
friendly by introducing 2 engines, clean output folder, and facility to
read unlimited number of pages. now there is no more inconvenience of
creating a user in advance of installation.
please. go through the read me carefully and give suggestions to improve
the package.
Read me easyocr 1.5 perfect for ubuntu 10.4. you can download from here
[http://code.google.com/p/easy-ocr/](http://code.google.com/p/easy-ocr/)

now a visually impaired person can read print using freely distributable
software.


Easy to install.
we have provided 3 types of installation mode. gui mode, easy mode, and
text mode.. first enter the easyocr package and extract it to your
computer and then go to the folder, select mode and enter. in gui mode
just tab to run and enter then follow the instructions.


easy installation

in this mode after entering the folder select easy installation and
enter and tab to select run and then enter password and wait . system
will reboot after installation automatically.

text mode installation

after entering the easyocr folder select text mode and enter. then tab
to run in terminal. then enter and do as instructed.


steps to be followed.

be careful to select a scanner which has full support of x sane.
1 after rebooting and connecting the scanner to the computer press super
+x to open x sane.
2 tab and come to -- directory /home/username/OCR/1.png and delete the
word username and write your username.
3 change colour to lineart,binary or gray (if there is no option as
written above you can proceed with colour option)
4 change brightness and resolution as needed resolution usually 300.
5 changing the rotation. if you are keeping the book or letter on the
scanner on 90 or 270 degree. please do the following. alt+tab to go to
preview menu and press shift tab to reach 000 combo box and change it to
90 or 270 as needed.

 a caution for visually impaired, please select 90 which comes below
000. Though, all the 4 changes will remain the same you will have to set
the rotation each time you open x sane.
6 alt tab again and come back to scanner menu. and press control+enter
for start scanning. now go on scanning as many number of pages as you
wish.
7 for converting and reading , press super+f9 and enter first page
number and last page number as asked by the programme. after the text
appeared you can use the reading key to read it.
please note that it is not the page number of the book but the number of
the page in the directory /home/username/OCR/1.png
8 if you are reading the document later, use super+f,  go to output file
to read your text material. you have pages and entire document here.
9 you can clear the output folder by pressing super+delete. .

10 there is facility for converting text in to wav format. super+a will
help you for it.and the output will appear on Desktop.


Special features

two engines.

easyocr 1.5 has two engines. you can select engine1 by pressing super+f1
(window key+f1) and engine2 super+f2.
engine1 is good for fast text conversion, and picture skipping
engine2 is , good for layout analysis.
both engines are almost 99 percent accurate in picking .
no limitation to number of pages and text conversion.

Now, one can go on scanning and convert the text by following steps

1 after scanning press supper+f9.
2 easyocr will ask you to enter the number of the beginning page and
then it will ask you to enter the number of end page. enter the number
and enter. then conversion will start and it is noteworthy that orca
will announce the number of the page being converted.

now after conversion the text will appear and you can press the add
button to read.

output folder is now clean.
at any time you can go to your text material by pressing super+f and
then output folder will appear. from the folder you can select any page
by pressing the number of the page and you can select your full text by
pressing first number of the page +dash.

you can clean the output folder by pressing super+delete.

reading letters or checking output quality.

super+1 will always read the first page in the directory.after opening x
sane by pressing super+x you can tab to the directory and change the
page number to 1.png and again tab to plus1 combo box and press  space
and bring it to 0 and now you will remain at the same page even after
scanning.

wav conversion.
you can convert the text in to wav by pressing super+a. As in the case
of text conversion, you can enter the page number and output will be
saved on the desktop.



easyocr is made as user friendly as possible. you can make it more
friendly through your suggestions. please contact the following emails.
[saatyan.kfb@gmail.com]("https://mail.google.com/mail/h/9ycnvr8jugf9/?v=b&cs=wh&to=saatyan.kfb@gmail.com")  and [nalin4linux77@gmail.com]("https://mail.google.com/mail/h/9ycnvr8jugf9/?v=b&cs=wh&to=nalin4linux77@gmail.com")


 Copyright (c) 2010  easy ocr development team

 All rights reserved .
 Redistribution and use in source and binary forms, with or without
modification,
 are permitted provided that the following conditions are met:

 * Redistributions of source code must retain the above copyright
notice,
 this list of conditions and the following disclaimer.
 * Redistributions in binary form must reproduce the above copyright
notice,
 this list of conditions and the following disclaimer in the
documentation
 and/or other materials provided with the distribution.
 * Neither the name of the  nor the easyocr team names of its
 contributors may be used to endorse or promote products derived from
this
 software without specific prior written permission.

 THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS
IS" AND
 ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED
 WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
 DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
LIABLE
 FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
CONSEQUENTIAL
 DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
OR
 SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
HOWEVER
 CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
LIABILITY,
 OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF
THE USE
 OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE."

[http://code.google.com/p/easy-ocr/](http://code.google.com/p/easy-ocr/)

---

