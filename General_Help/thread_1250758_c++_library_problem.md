---
title: "c++ library problem"
date: 2009-08-26
forum: General Help
---

### Post by chunkumonkey on 2009-08-26
I am working on a class project and I can't seem to compile the code on my computer. It gives me the following errors when I try to compile all the parts of the project.

sahil@ubuntu:~/Documents/src$ gcc -o node node.cpp recv_sock.cpp send_sock.cpp -lsocket -lthread -lnsl
node.cpp:4:20: error: thread.h: No such file or directory
node.cpp:37: error: ‘thread_t’ does not name a type
node.cpp:41: error: ‘::main’ must return ‘int’
node.cpp: In function ‘int main(int, char**)’:
node.cpp:53: error: ‘routerTid’ was not declared in this scope
node.cpp:53: error: ‘thr_create’ was not declared in this scope
node.cpp:71: error: ‘electionThreadTid’ was not declared in this scope
node.cpp:76: error: ‘thr_join’ was not declared in this scope
node.cpp: In function ‘void broadcastMessage(int, int)’:
node.cpp:115: warning: deprecated conversion from string constant to ‘char*’
node.cpp: In function ‘void* messageRouter(void*)’:
node.cpp:150: error: ‘electionThreadTid’ was not declared in this scope
node.cpp:150: error: ‘thr_create’ was not declared in this scope
node.cpp:168: error: ‘leaderTid’ was not declared in this scope
node.cpp:168: error: ‘thr_create’ was not declared in this scope
node.cpp: In function ‘void* electionThread(void*)’:
node.cpp:307: warning: deprecated conversion from string constant to ‘char*’
node.cpp:324: error: ‘heartBeatTid’ was not declared in this scope
node.cpp:324: error: ‘thr_create’ was not declared in this scope
node.cpp:333: error: ‘leaderTid’ was not declared in this scope
node.cpp:333: error: ‘thr_create’ was not declared in this scope
node.cpp: In function ‘void* heartBeatMonitor(void*)’:
node.cpp:359: error: ‘electionThreadTid’ was not declared in this scope
node.cpp:359: error: ‘thr_create’ was not declared in this scope
recv_sock.cpp: In member function ‘int RecvSock::recvMsg(MESSAGE*)’:
recv_sock.cpp:63: error: invalid conversion from ‘int*’ to ‘socklen_t*’
recv_sock.cpp:63: error:   initializing argument 3 of ‘int accept(int, sockaddr*, socklen_t*)’

Any suggestions? I know I don't have the c++ libraries because it doesn't recognise sys/socket.h aswell as  a standard library. How do I correct this?

---

### Post by Brandon Williams on 2009-08-27
First, you should probably post these types of questions in the programming talk forum, not general help.

Next, I'm not sure what thread library you're trying to use, but all of the errors in your listing are related to this. Typically, for threads programming on Linux, you would include pthread.h (not thread.h), and all of the function names would start with pthread (not thr). Make sure that you have manpages-posix-dev installed, and then view the man pages for pthread_create and pthread_join for more information.

And finally, what gives you the indication that sys/socket.h isn't recognized? There's nothing about it in your compiler output. Did you install build-essential?

---

