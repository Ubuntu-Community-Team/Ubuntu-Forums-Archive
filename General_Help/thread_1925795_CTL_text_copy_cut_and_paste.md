---
title: "CTL text copy cut and paste"
date: 2012-02-15
forum: General Help
---

### Post by wijit on 2012-02-15
Already searched but found no similar problem. May be I'm in a very small subset of Ubuntu. Most of my works are in Thai which is one of CTL styles of fonts. Problem I'm going to discuss here is very new since it happenned not more than 2 months ago. More than 3 years that I have been using Ubuntu I have never found it. Cut/copy and paste text is what I do everyday. Now I have to be careful when doing it because Thai text sometime changes to a string of question marks. Since there are 3 methods of doing the job and several situation (direction) for text moving as well as more than 2 character codes that involve presentation of text, I don't think I can tract all kinds of the combination. Here are some kinds of them:

Environmental: Acer TravelMate 4720, Ubuntu 10.04
Source Text: Thai text
Analysed by ways of doing:
The left most column contains applications where source text resides.
The top row contains applications where text is pasted to.
1. Selecting source and middle mousing:
-------	gmail	gedit	Writer	Calc(text box)	Calc(cell)
gmail	OK	OK	OK	OK	OK
gedit	OK	OK	OK	OK	OK
Writer	OK	OK	OK	OK	OK
Calc(text box)	OK	OK	OK	OK	OK
Calc(selected single cell)	OK	OK	Blank Object	OK	OK

2. Selecting and Ctrl+c source and Ctrl+v:
-------	gmail	gedit	Writer	Calc(text box)	Calc(cell)
gmail	???	OK	OK	???	OK
gedit	???	OK	OK	OK	OK
Writer	OK	OK	OK	OK	OK
Calc(text box)	OK	OK	OK	???	???
Calc(selected single cell)	???	???	???	???	???

3. Main menu Edit > Copy source and Edit > Paste:
-------	gmail	gedit	Writer	Calc(text box)	Calc(cell)
gmail	???	OK	OK	OK	OK
gedit	???	???	???	???	???
Writer	???	???	???	???	???
Calc(text box)	???	OK	OK	OK	???
Calc(selected single cell)	???	OK	Blank Object	OK	OK

There are many of ways that I did not explore such as getting source by menuing and then pasting by Ctrl+v 'ing, etc., or even a pop-up or a context menu.
This problem has never occured with English text.

---

