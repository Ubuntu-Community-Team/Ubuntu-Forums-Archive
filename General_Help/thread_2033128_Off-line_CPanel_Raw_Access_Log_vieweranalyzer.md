---
title: "Off-line CPanel Raw Access Log viewer/analyzer?"
date: 2012-07-25
forum: General Help
---

### Post by CoolBreeze47 on 2012-07-25
Hi there

In CPanel>Logs>Raw Access Logs there is a place where you can download the raw access logs for a particular domain. However, there doesn't seem to be any way of viewing them through Gedit, Kate or other standard text file viewer because the file is quite large.

Is there a downloadable program for Ubuntu that can be installed and used off-line/locally to view/analyze raw access logs?. I want to be able to download these logs and view them on the computer rather than online. Also, I would need a log viewer/analyzer with a GUI/frontend if possible. Does anything like this exist?.

Thanks so much!, CB

---

### Post by cariboo on 2012-07-25
Have you tried in a terminal:

```
cat <log_file> | less
```

press the space bar to go to the next page

---

### Post by CoolBreeze47 on 2012-07-25
Thanks for that. It worked perfectly and loaded fast. I even tried just the "cat <log_file>" by itself. Is there a command to display the log file in it's entirety so it can be searched?.

- Thanks again 

> **cariboo907 said:**
> Have you tried in a terminal:

```
cat <log_file> | less
```press the space bar to go to the next page

---

### Post by Cheesemill on 2012-07-25
> **cariboo907 said:**
> Have you tried in a terminal:

```
cat <log_file> | less
```press the space bar to go to the next page
For you cariboo907, a '[Useless Use of Cat Award]("http://partmaps.org/era/unix/award.html")' :).
In fact by using cat you are losing one of the main features of less which is it only loads part of the file into memory at once, it doesn't have to load the whole thing.
Just use less by itself:
```
less <filename>
```As well as using the space bar you can use the cursor and page up/down keys to navigate.
To search for a specific term just type:
```
/<term>
```and hit Enter. To go to the next occurrence hit n.

I actually install the application 'most' on all of my systems and use it instead. It works in exactly the same way as less but has more features:
> [NOPARSE]DESCRIPTION
       most is a paging program that displays, one windowful at a time, the contents of a file on a terminal.  It pauses after each windowful and prints on the win&#8208;
       dow status line the screen the file name, current line number, and the percentage of the file so far displayed.

       Unlike other paging programs, most is capable of displaying an arbitrary number of windows as long as each window occupies at least two screen  lines.   Each
       window  may contain the same file or a different file.  In addition, each window has its own mode.  For example, one window may display a file with its lines
       wrapped while another may be truncating the lines.  Windows may be `locked' together in the sense that if one of the locked windows scrolls, all locked  win&#8208;
       dows  will scroll.  most is also capable of ignoring lines that are indented beyond a user specified value.  This is useful when viewing computer programs to
       pick out gross features of the code.  See the `:o' command for a description of this feature.

       In addition to displaying ordinary text files, most can also display binary files as well as files with arbitrary ascii characters.  When a file is read into
       a  buffer,  most  examines the first 32 bytes of the file to determine if the file is a binary file and then switches to the appropriate mode.  However, this
       feature may be disabled with the -k option.  See the description of the -b, -k, -v, and -t options for further details.

       Text files may contain combinations of underscore and backspace characters causing a printer to underline or  overstrike.   When  most  recognizes  this,  it
       inserts the appropriate escape sequences to achieve the desired effect.  In addition, some files cause the printer to overstrike some characters by embedding
       carriage return characters in the middle of a line.  When this occurs, most displays the overstruck character with a bold attribute.   This  feature  facili&#8208;
       tates  the  reading  of UNIX man pages or a document produced by runoff.  In particular, viewing this document with most should illustrate this behavior pro&#8208;
       vided that the underline characters have not been stripped.  This may be turned off with the -v option.

       By default, lines with more characters than the terminal width are not wrapped but are instead truncated.  When truncation occurs, this is indicated by a `$'
       in the far right column of the terminal screen.  The RIGHT and LEFT arrow keys may be used to view lines which extend past the margins of the screen.  The -w
       option may be used to override this feature.  When a window is wrapped, the character `\' will appear at the right edge of the window.
[/NOPARSE]

---

### Post by CoolBreeze47 on 2012-07-26
Thanks for all the help folks. I finally decided on grep...

grep <searchword> <logfile>

Worked like a charm and I was able to find a tidy list of search results for exactly what I was looking for. Took a minute or two to do the search but other than that, perfect.

---

