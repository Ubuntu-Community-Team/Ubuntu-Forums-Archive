---
title: "Evolution experiment"
date: 2011-10-05
forum: General Help
---

### Post by Hector23 on 2011-10-05
Right-click on the desktop and create a file called Evolution.txt. Open it and write: "This is my original message". Save, close.

Open Evolution. 

Shift + CTRL + M.

Message to: [email]toto@xxwhatever.org[/email]
Subject: Whatever

In the message area:

"Hello Toto!"

CTRL + M

Add Evolution.txt as an attachment.

Save as draft, close.

If you look at the attachment in Evolution's draft box, you'll see it exactly as typed.

Now, go back to the desktop. Reopen the Evolution.txt file and add: "This has been added."

Save and close.

Go back to Evolution and see if the change appears in the attachment. It doesn't.

If you open the message with the "down arrow beside a paper sheet" icon at the bottom, it opens this file:

/~/.evolution/cache/tmp/evolution-user-Foo123/Evolution.txt

in read-only mode.

So, it's not the original on the Desktop that is sent, it's the file in /~/.evolution/cache/tmp/evolution-user-Foo123/
and this one doesn't receive additional changes to the original file. The only way to send the file as it has been modified, is to delete the attachment and reselect the file on the desktop. Then only, will a new file will be created in /~/.evolution/cache/tmp/evolution-user-Foo123/.

I believe the user should at least be advised that it's not the original that is being sent but a copy made when the message was originally saved. There should be a warning if the original and the copy differ. What's more, I haven't seen any warning in the documentation to explain how attachments work.

---

### Post by hwttdz on 2011-10-05
I understand where you're coming from but I actually think the current setup is the most intuitive.  Perhaps it would be nice to also have the option to insert a link to an attachment, so that it will grab the attachment when you send (sort of like links to objects in open office, where the document updates the object when you update the object file).  

I don't use drafts much, but the current behavior is the behavior I would expect.  It also saves people from deleting a file before they've sent it.

---

### Post by Hector23 on 2011-10-05
> **hwttdz said:**
> I understand where you're coming from but I actually think the current setup is the most intuitive.(...) the current behavior is the behavior I would expect

You think you should intuitively know that the file that will finally be sent is the one in /~/.evolution/cache/tmp/evolution-user-Foo123/Evolution.txt ???

I believe it's the worst software nightmare a so-called enterprise quality OS can face.

Imagine. It's late. You want to send a letter to your boss (or ex-wife, whatever) and, just before you hit send, you think maybe you should read it again the following morning.

You modify the file, remove typos or insults and it's finally the previous copy that gets sent.

Do you really find it's OK because people should intuitively know that it's a copy in the cache that will finally get sent?

> **hwttdz said:**
> It also saves people from deleting a file before they've sent it.

I certainly like to keep a copy of attachments I send. 

If I accidentally deleted a file, I wouldn't expect it to be sent and I'd take it back from the trash can.

Intuitively, that's what *I* believe should make sense.

If I ran a company, I'd be furious to be offered software such as Evolution. Meanwhile, Canonical is working on interfaces...

---

### Post by hwttdz on 2011-10-05
> You think you should intuitively know that the file that will finally be sent is the one in /~/.evolution/cache/tmp/evolution-user-Foo123/Evolution.txt ???

Well, I would expect it to send the version I attached, in much the same way if I were to put a document in an envelope and later edit the document on my computer I'd expect the original version to still be in the envelope.

> I certainly like to keep a copy of attachments I send.

That's nice, but I can also see someone saying, "I thought I saved that document as an attachment to a draft, now I've lost my file!". Also, if you edit the file, then your file no longer matches the version everyone else received.  

As I said, it would be nice to have the choice to either attach a real document, or attach a link to a live document.  

11.10 actually switches to using thunderbird by default, so now you can be angry at mozilla.  Also, it unless the draft is saved locally there is no possibility of this.  And if the draft is saved locally, I'd have to go back to the same machine to actually send the message.

A sort of solution is to actually leave the compose window up with thunderbird and it will wait until you press send to grab a copy.

Another solution would be just giving them a link to a document.  That way you can edit to your hearts content, and everyone can get whatever version's up.

---

### Post by Hector23 on 2011-10-06
> **hwttdz said:**
> Well, I would expect it to send the version I attached, in much the same way if I were to put a document in an envelope and later edit the document on my computer I'd expect the original version to still be in the envelope.

The problem is, here, you believe that the letter is still on your desktop, not in a hidden envelope somewhere in a cache that you never heard of.

That's going to be it for me.

---

### Post by dcstar on 2011-10-06
> **hwttdz said:**
> Well, I would expect it to send the version I attached, in much the same way if I were to put a document in an envelope and later edit the document on my computer I'd expect the original version to still be in the envelope.
........
+1.

These other "arguments" are just from someone who doesn't comprehend that a sent e-mail is a separate entity in itself, and anything external to it is just that and now has NOTHING to do whatsoever to the e-mail that has been previously sent.

---

