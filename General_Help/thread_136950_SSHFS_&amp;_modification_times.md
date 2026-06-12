---
title: "SSHFS &amp; modification times"
date: 2006-02-27
forum: General Help
---

### Post by batkins on 2006-02-27
I'm using SSHFS to mount a remote directory on my filesystem.  It seems to be working fairly well, except that modification times don't get written to the files in the directory.  So when I save a file in Emacs, it writes the new modification time to the filesystem, but the mtime doesn't actually change.  If i then try to save the file again, Emacs warns me that the file has changed since the last save and confirms that I actually want to save the file.  This gets pretty annoying.  Is there any way to resolve this issue?

---

### Post by batkins on 2006-02-28
Just in case someone has this problem in the future, I got around it with:
```

(defun revert-if-necessary ()
  (when (and buffer-file-name
	     (string-match "/home/bill/net" buffer-file-name))
    (revert-buffer nil t)))

(add-hook 'after-save-hook 'revert-if-necessary)

```
in my .emacs.  Obviously, you have to change "/home/bill/net" to wherever your SSHFS mounts are.

---

