---
title: "SCTP problem"
date: 2009-11-28
forum: General Help
---

### Post by weishigoname on 2009-11-28
I am using ubuntu 9.04 ,and I want to program with SCTP .First ,I check the header file ,find out there is not  "netinet/sctp.h".so  use:
     sudo apt-get install libsctp-dev lksctp-tools
install it ,and follow the website [http://lksctp.sourceforge.net/overview.html](http://lksctp.sourceforge.net/overview.html) 
after that the header "netinet/sctp.h" is included in /usr/include/
but when I compile my program :
 gcc -g sctp_client.c -o client
/tmp/ccg2R9PE.o: In function `sctpstr_cli_echoall':
/home/ws/download/kernelproject/workspace/sctp/sctp_client.c:38: undefined reference to `sctp_sendmsg'
/home/ws/download/kernelproject/workspace/sctp/sctp_client.c:43: undefined reference to `sctp_recvmsg'
/tmp/ccg2R9PE.o: In function `sctpstr_cli':
/home/ws/download/kernelproject/workspace/sctp/sctp_client.c:67: undefined reference to `sctp_sendmsg'
/home/ws/download/kernelproject/workspace/sctp/sctp_client.c:70: undefined reference to `sctp_recvmsg'
collect2: ld returned 1 exit status

I do not know how to do now .

---

