---
title: "Can't boot Wubi version of Ubuntu 10.04"
date: 2010-12-05
forum: General Help
---

### Post by krispin on 2010-12-05
I have been running Ubuntu (Wubi) for about 2 - 3 months now and it has been flawless. 

I start up the computer. I get the choice to book windows 7 or Ubuntu I choose Ubuntu and then I get the list of boot installers to choose from and it is play time. 

Today when I went to get onto my Ubuntu install, I got the first window asking if I want Windows or Ubuntu and when I chose Ubuntu, rather than going to the Grub boot menu, the laptop would just restart and go back to the first window asking if I wanted windows 7 or Ubuntu.

It seems the Grub boot files are gone. Now I have read that the fix for this is to use a live disk of Ubuntu to reinstall Grub2 BUT it is my impression the Wubi does not install Ubuntu "normally"

My question is (finally)... Can I rescue Grub using a live disk as if ubuntu was installed directly yo a partition from a regular ISO or is there another way to do it if it was installed by Wubi?

Thanks in advance

---

### Post by bcbc on 2010-12-05
> **krispin said:**
> I have been running Ubuntu (Wubi) for about 2 - 3 months now and it has been flawless. 

I start up the computer. I get the choice to book windows 7 or Ubuntu I choose Ubuntu and then I get the list of boot installers to choose from and it is play time. 

Today when I went to get onto my Ubuntu install, I got the first window asking if I want Windows or Ubuntu and when I chose Ubuntu, rather than going to the Grub boot menu, the laptop would just restart and go back to the first window asking if I wanted windows 7 or Ubuntu.

It seems the Grub boot files are gone. Now I have read that the fix for this is to use a live disk of Ubuntu to reinstall Grub2 BUT it is my impression the Wubi does not install Ubuntu "normally"

My question is (finally)... Can I rescue Grub using a live disk as if ubuntu was installed directly yo a partition from a regular ISO or is there another way to do it if it was installed by Wubi?

Thanks in advance

You shouldn't reinstall grub from a live cd - this will break windows.

You need to read this - it's a general summary of the issue and fix:
[http://ubuntuforums.org/showpost.php?p=10183394&postcount=87](http://ubuntuforums.org/showpost.php?p=10183394&postcount=87)

For more specific details, you can see 
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

And just ask if you have issues.

---

### Post by krispin on 2010-12-06
Thanks BCBC, I am just going through the documentation right now.

---

