---
title: "WTF happened to my server?!?!?!"
date: 2006-02-15
forum: General Help
---

### Post by rensu on 2006-02-15
I get spammed on server this error:
postdrop: warning: mail_queue_enter: create file maildrop/540021.11665: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/824479.11716: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/900908.11747: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/754467.11702: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/963881.11744: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/171483.11710: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/244386.11670: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/305259.11690: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/772434.11713: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/540021.11665: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/824479.11716: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/900908.11747: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/754467.11702: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/963881.11744: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/171483.11710: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/244386.11670: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/305259.11690: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/772434.11713: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/540021.11665: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/824479.11716: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/900908.11747: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/754467.11702: Read-only file system


GETTING THIS ERROR SPAMMED ON SCREEN!??!?
What happened to my server?! Can someone help me plz:(((((((

---

### Post by anirban.sam on 2006-02-15
try from a console,

ps ax | grep postfix, next note the process id, next,
sudo kill <process id>

---

