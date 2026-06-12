---
title: "Permissions: Write without read?"
date: 2011-03-09
forum: General Help
---

### Post by scangirl on 2011-03-09
Is it possible to give write permissions but not read for a directory?

I mean, I need a user to upload files to a directory but can not see them once uploaded (in case of data privacy)

Any help will be appreciate ):P

---

### Post by mörgæs on 2011-03-09
Yes, **chmod** can do that. 

You can learn more of chmod in the handbook in my signature.

---

### Post by scangirl on 2011-03-10
Hello mörgæs, thanks for your response.

I know chmod and I know how it works. The problem is that I need that user has permissions to write but not to read and I think chmod is cumulative (if he/she can write, then can read) Am I wrong? Is there any way I can access through sftp and upload files but not see the contents of the dir?

Thanks a lot.:D

---

### Post by lithopsian on 2011-03-10
Come one, you can check this yourself very easily  Permissions are not "cumulative".  If you remove read permission then nobody will be able to read even if they can write.

However, this might not quite solve your problem.  If you remove read permission from a directory, but leave write permission, people will be able to create files in the directory but will not be able to list the contents of the directory.  However, the files that they create will by default still have both read and write permission for the owner and read permission for everyone else.  People could still potentially read files although they might find it difficult to know they were there.  You could solve this issue with umask so that files were created with no read permissions.

---

