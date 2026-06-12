---
title: "Installing IDA pro in Ubuntu"
date: 2011-10-27
forum: General Help
---

### Post by Muteb on 2011-10-27
Hi everyone, 

Please, anyone knows how i can install IDA pro in Ubuntu? i am working with volatility freamwork forensic tools, and one of its tools need me to use ida 

i was able to install ida in wine but that was not help. it has to be in ubuntu becasue once i but the directory of  wine in tool, does not recognize it. 

the tool need the idal

here is the description of the tools in Volatility freamwork 

[http://code.google.com/p/volatility/wiki/CommandReference#threads](http://code.google.com/p/volatility/wiki/CommandReference#threads)
**ssdt_ex**

If  you want to explore SSDT hooks installed by rootkits, use the ssdt_ex  command. This will automatically detect which SSDT functions are hooked,  extract the hooking kernel driver to disk, and generate an IDC file  (IDA script) containing labels for the rootkit functions. Then, if you  have idag.exe (Windows) or idal (Linux/OS X) in your $PATH, then it will  create an IDB file from the extracted kernel driver and run the IDC  script. The result is a pre-labeled IDB for you to explore and reverse  engineer, after typing just one command in Volatility. 


Thanks

---

