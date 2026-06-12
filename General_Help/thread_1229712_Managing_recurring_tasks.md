---
title: "Managing recurring tasks"
date: 2009-08-02
forum: General Help
---

### Post by MeKino on 2009-08-02
Hi,

I've been trying to find a way of managing recurring tasks and came across this "old" post:

=================================================================
 Re: Managing recurring tasks
I'm searching to see if xvtdl has been ported from OpenWindows.

If it has been ported it will meet your needs. I used it well over a decade ago on different architectures and unices. Here's an excerpt from the .readme I have:

* You can manage multiple todo lists; lists can have sublists.
* Each todo list item is prioritized; each list can be displayed in
a combination of priority, chronological, and alphabetical
order.
* List items, if you do not "check them off", will propagate from
one day to the next.
* List items can be recurring items, i.e., items that will
automatically pop up weekly, biweekly, monthly, etc. These items
will propagate like "normal" list items.
* List items can have deadlines associated with them, with several
types of actions that execute on or after a deadline.
* List items can have annotations associated with them. Annotations
are edited with a "normal" text editor.
* You can set list items on any day, with easy calendar management.
* Lists can be printed on a "plain" or Postscript printer.
* Printing/display supports ISO 8859.1 character set.
* List items can be logged when checked on/off with optional comments
added to the log file.
* List items can be retained or deleted when checked off.
* Multiple lists can be combined for viewing or printing.
* Multiple lists from multiple files can be manipulated.
* Changes to the todo list can be made and are detected by the running
programs.


Update:
XView libraries needed for xvtdl appear to have been ported to Linux. See [http://www.physionet.org/physiotools/xview/](http://www.physionet.org/physiotools/xview/)
Next get the xvtdl-5.2msj.tar.gz sources from [http://step.polymtl.ca/~coyote/XView/apps/xvtdl/](http://step.polymtl.ca/~coyote/XView/apps/xvtdl/)
Then, you *should* be able to compile it against the XView libraries

If I get some free time in the next day or two I'll try and get this built on my Ubuntu 64-bit Gutsy install on my T61p.

Hope this helps
Last edited by r m h; April 8th, 2008 at 01:15 AM.. Reason: update

==================================================================

I've downloaded the libraries and the tar.gz files but I've not really done much in the way of compiling and could do with some kind person just talking me through the steps - as I don't know what to do next!

Thanks in advance...

---

