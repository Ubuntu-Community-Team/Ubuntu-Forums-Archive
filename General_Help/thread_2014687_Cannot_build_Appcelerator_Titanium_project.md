---
title: "Cannot build Appcelerator Titanium project"
date: 2012-07-02
forum: General Help
---

### Post by kreoton on 2012-07-02
Hi,

First of all sorry if this is not right forum for such questions, but I cannot find answer anywhere else on Internet.
I'm using Ubuntu 12.04 (x64) and using newest Appcelerator Titanium version. Whenever I try to build Android I always get this error:

```
[ERROR] Exception occured while building Android project:
[ERROR] Traceback (most recent call last):
[ERROR]   File "/home/irmantas/.titanium/mobilesdk/linux/2.1.0.GA/android/builder.py", line 2206, in <module>
[ERROR]     s.build_and_run(False, avd_id, debugger_host=debugger_host)
[ERROR]   File "/home/irmantas/.titanium/mobilesdk/linux/2.1.0.GA/android/builder.py", line 2037, in build_and_run
[ERROR]     launched, launch_failed = self.package_and_deploy()
[ERROR]   File "/home/irmantas/.titanium/mobilesdk/linux/2.1.0.GA/android/builder.py", line 1569, in package_and_deploy
[ERROR]     self.keystore_alias])
[ERROR]   File "/home/irmantas/.titanium/mobilesdk/linux/2.1.0.GA/android/run.py", line 36, in run
[ERROR]     process = subprocess.Popen(args, stderr=subprocess.PIPE, stdout=subprocess.PIPE)
[ERROR]   File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
[ERROR]     errread, errwrite)
[ERROR]   File "/usr/lib/python2.7/subprocess.py", line 1249, in _execute_child
[ERROR]     raise child_exception
[ERROR] OSError: [Errno 2] No such file or directory
```

Full build.log can be found here [http://pastebin.com/c02Tjr8K](http://pastebin.com/c02Tjr8K)

JAVA version is 1.6.0_32

Thanks for your time and help

---

### Post by IamPersistent on 2012-07-14
I posted my solution on [StackOverflow]("http://stackoverflow.com/a/11482718/434316") There are also some suggestions from the VisualIDE folks over there also.

---

### Post by wlaurance on 2012-07-25
Nevermind read stack overflow

---

