---
title: "Package manager is broken"
date: 2010-12-08
forum: General Help
---

### Post by maxrpowell on 2010-12-08
I just installed brother DCP-350c drivers from [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090")
When I finished I tried to install a scanner driver from brother.
My package manager is broken.
The page mentioned something about that [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090")(just a scroll down)
I tried what they said but the manager is still broken.
It gives me this error report:

 	Quote:
 	 	 		 			 				Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the dcp350clpr package. This might mean you need to manually fix this package.

 
it looks as if all I must do is uninstall package dcp350clpr
i cannot use sudo apt-get remove dcp350clpr
b/c package manager is broken

how can i do that?
	 	 
Ubuntu 10.10 on Toshiba Satellite
 		                   		  		  		 		 			 		 		  		  		  	   	 		 
  		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] []("http://ubuntuforums.org/editpost.php?do=editpost&p=10216243")    		 		 		 		 		 			 		 		 		 	       	 	 		maxrpowell 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=937459") 	 	 		[Send a private message to maxrpowell]("http://ubuntuforums.org/private.php?do=newpm&u=937459") 	 	 	 	 		[Find More Posts by maxrpowell]("http://ubuntuforums.org/search.php?do=finduser&u=937459") 	 	 	[Add maxrpowell to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=937459")

---

