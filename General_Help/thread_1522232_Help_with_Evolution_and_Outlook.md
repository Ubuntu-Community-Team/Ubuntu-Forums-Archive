---
title: "Help with Evolution and Outlook"
date: 2010-07-01
forum: General Help
---

### Post by X-Windows on 2010-07-01
So in about one month I'm heading off to college and would like to work out the few remaining bugs in my Ubuntu-Windows dual-boot. Along with some other minor issues I cant seem to get Evolution and Outlook (2010) to play nice...

I am using a Gmail account as my primary email, and have it configured on both evolution and Outlook. As far as I can tell, I have only two options: leave mail on the server and use a client to manipulate it, or download all mail and handle it on the computer.

I'm not sure how you all setup your dual-boot email setups but I'm stumped. I cant get Evolution to handle IMAP right (can read mail but not delete or move it), and I cant find a way to get Outlook and Evolution to share mail once it is downloaded off the server. What is the best way to handle this, and how did you all do it?

---

### Post by duanedesign on 2010-07-01
On the Evolution FAQ i noticed this.

>  **I copied some messages to another folder but when I unselect View->Hide Deleted Messages I see they're still there. Why?**

On IMAP servers, Evo moves messages by copying and deleting (IMAP has no "move" operation). Deleting means "mark for deletion" so the original messages are still there until you do an Expunge or Empty Trash (see previous question). For consistency, it also does this on other types of account

---

### Post by X-Windows on 2010-07-02
That didn't seem to help, or I don't understand it correctly. Is there a way to run a dual-boot email setup? Ideally all the mail remains on the server and is accessed by clients (Evolution and Outlook).

In theory (probably incorrect) as long as the mail stays on a server, any client should be able to issue a "delete" command and have the server trash it. It doesn't seem to be that simple though, and my only other alternative is to download mail and sync between outlook and evolution.

Has anyone else successfully managed dual-boot email clients?

---

