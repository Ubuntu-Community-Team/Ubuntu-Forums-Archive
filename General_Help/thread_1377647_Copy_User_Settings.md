---
title: "Copy User Settings"
date: 2010-01-10
forum: General Help
---

### Post by paddy100 on 2010-01-10
Hi there, First post of many....... Here goes

I have 2 users and I would like to copy all the files and folders in one home dir to another.... sounds simple, til i got started.  Ive tried

```
sudo cp -nRv /home/user1/* /home/user2
```but that didnt copy the .* folders. Im after the firefox and thunderbird folders mainly, but all of them is OK too.

im talking about the .adobe, .amsn .......... 

How can I copy the .* folders from one user home folder to another and then give the correct permissions to the new user.

Thanks in advance

---

### Post by michy99 on 2010-01-10
I'm not sure that's a good idea. The hidden configuration files and folders will be created for the new user whenever they run the application.

---

### Post by warfacegod on 2010-01-10
Are you looking to make a backup? This is what I do with some modifications:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by paddy100 on 2010-01-10
> I'm not sure that's a good idea. The hidden configuration files and folders will be created for the new user whenever they run the application.

I thought the hidden folders were the configuration settings? so if I copy the .mozilla folder from one home folder to another they would have all the favourites, cookies, history, etc....

Im only getting into this Ubuntu thingy, and still thinking in Windows language.... so in Windows you can do it by copying these folders to the profile folders.... you must be able to do it in Ubuntu!!

---

### Post by junapp on 2010-01-10
maybe this will help, not sure but worth a shot:
[http://www.labtestproject.com/linuxcommand/copy_contents_of_directory_include_hidden_files_and_hidden_directory_using_cp_command](http://www.labtestproject.com/linuxcommand/copy_contents_of_directory_include_hidden_files_and_hidden_directory_using_cp_command)
or
[http://www.linuxquestions.org/questions/linux-newbie-8/how-do-you-copy-hidden-files-from-one-directory-to-another-387107/](http://www.linuxquestions.org/questions/linux-newbie-8/how-do-you-copy-hidden-files-from-one-directory-to-another-387107/)

---

