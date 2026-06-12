---
title: "Permissions for Media Files"
date: 2011-07-27
forum: General Help
---

### Post by satish_j on 2011-07-27
I wanted to know whether its possible to prevent some user from playing mp3/any other media files, using the chmod command?
Are the read and execute bits meant only for text/office files?

---

### Post by Ghost_Mazal on 2011-07-27
> **satish_j said:**
> I wanted to know whether its possible to prevent some user from playing mp3/any other media files, using the chmod command?
Are the read and execute bits meant only for text/office files?

No permissions are for all files. So you can certainly block access to media files with chmod

---

### Post by lrgmmc on 2011-07-27
```
chmod 700 "file or folder name"
```
That will make it were no one but you can use those files.

---

### Post by satish_j on 2011-07-28
> **lrgmmc said:**
> ```
chmod 700 "file or folder name"
```
That will make it were no one but you can use those files.

I thought chmod 744 will prevent all but me from playing media files since thye will only have 'REad' rights.
chmod700 will not even show them the media files in a directory..Right?

---

### Post by mcduck on 2011-07-28
> **satish_j said:**
> I thought chmod 744 will prevent all but me from playing media files since thye will only have 'REad' rights.
chmod700 will not even show them the media files in a directory..Right?

reading a file doesn't mean "reading a text file", it's the permissions to open a file and access it's contents. So to play a music file you'd need to read the music file.

(if you thought the execute permissions was what would prevent you from accessing media files, it's not. Execute permission only defines if a file may be executed as a program or not.)

For a file:
- read = access and display (or play, view, whatever) a file's contents
- write = modify a file's contents
- execute = run the file as a program. (binary files, shell scripts etc.)

...and for a directory:
- read = list contents of a directory
- write = create new files and modify files in that directory
- execute = change your location into the directory (as in open it with a file manager, or cd into it in command line)

( so if you have a directory with execute permission but no read permission, you are able to run programs and open files in it if you know the full path and filename. But you can't actually see the files in there)

---

### Post by satish_j on 2011-07-28
> **mcduck said:**
> reading a file doesn't mean "reading a text file", it's the permissions to open a file and access it's contents. So to play a music file you'd need to read the music file.

(if you thought the execute permissions was what would prevent you from accessing media files, it's not. Execute permission only defines if a file may be executed as a program or not.)

For a file:
- read = access and display (or play, view, whatever) a file's contents
- write = modify a file's contents
- execute = run the file as a program. (binary files, shell scripts etc.)

...and for a directory:
- read = list contents of a directory
- write = create new files and modify files in that directory
- execute = change your location into the directory (as in open it with a file manager, or cd into it in command line)

( so if you have a directory with execute permission but no read permission, you are able to run programs and open files in it if you know the full path and filename. But you can't actually see the files in there)

Ok,so the read permission is what is reqd to play media files.
You did not answer my other query..Does chmod 700 will effectively block all but owner of file from viewing file
Am i right?

---

### Post by mcduck on 2011-07-28
> **satish_j said:**
> Ok,so the read permission is what is reqd to play media files.
You did not answer my other query..Does chmod 700 will effectively block all but owner of file from viewing file
Am i right?

yes, it removes all permissions from anybody else than you, even from those that are in same group as you.

---

