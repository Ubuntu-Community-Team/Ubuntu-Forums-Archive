---
title: "question about using vm on imap folders"
date: 2011-08-16
forum: General Help
---

### Post by paper_brdige on 2011-08-16
I have configured emacs to use vm as a mail reader.

I have one primary e-mail account, which is an IMAP account provided by my employer.

I seem to have set everything up correctly, with gnutls, stunnel, etc., because I managed to see my imap folders in emacs.

The problem is that most of the folders (including the server inbox folder, which I set as my default inbox), I only managed to view once. Now when I try to view them, they appear empty (although I can verify that they aren't), and the message buffer says that the auto-saved version is newer. I think that vm is looking into a chache file instead of the server folder. After I noticed this problem, I accessed a few other folders that I'd not yet read, and I was careful to quit viewing them WITHOUT autosaving or caching, and I can still view those folders, repeatedly.

I cannot figure out how to view my inbox or the few other folders that I initially viewed, though.

From my .emacs :


(add-to-list 'load-path
(expand-file-name "~/vm-8.1.0-1/lisp"))
(add-to-list 'Info-default-directory-list
(expand-file-name "~/vm-8.1.0-1/info"))
(require 'vm-autoloads)
(setq vm-stunnel-program "/usr/bin/X11/stunnel4")


(autoload 'vm "vm" "Start VM on your primary inbox." t)


From my .vm  (infact this is the entire file):

(setq vm-imap-account-alist
           '(
             ("imap-ssl:imap.nd.edu:993:*:login:cfranks:*" "ND")
            )
     )

(setq vm-primary-inbox "imap-ssl:imap.nd.edu:993:inbox:login:cfranks:*")

---

