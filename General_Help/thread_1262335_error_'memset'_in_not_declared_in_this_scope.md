---
title: "error: 'memset' in not declared in this scope"
date: 2009-09-09
forum: General Help
---

### Post by ricky845 on 2009-09-09
'memset' is not declared in this scope.

anyone knows why is this error??

thanks

---

### Post by baseface on 2009-09-09
a little information on what youre doing when you get that error would probably help.

---

### Post by ricky845 on 2009-09-09
i'm doing the "make". it is a c/s application using multicast DNS

---

### Post by baseface on 2009-09-09
if you can post the code and the entire error message i can look at it for you.

---

### Post by ricky845 on 2009-09-09
her is the error:

void mDNSObserver::run() {
          int nbytes,addrlen;
          char msgbuf[MSGBUFSIZE];
          cout << "mDNSObserver: running" << endl;
        memset(msgbuf,0,sizeof(msgbuf));
          // Now just enter a read-print loop.
          while (this->keepRunning) {
           ...

i get 2 more and the codes are similar:

mDNSObserver::mDNSObserver(mNameServer* c): client(c), keepRunning(true) { 
        struct ip_mreq mreq; 
        u_int yes=1; 
        // Set up multicast group destination address for receiving. 
        if ((fd4Receiving=socket(AF_INET,SOCK_DGRAM,0)) < 0) { 
            cerr << "Problems creating receiving multicast socket" << endl; 
            exit(1); 
        } 
        // Trick just to allow multiple sockets to use the same PORT number: Only to try several processes in the same machine. 
        if (setsockopt(fd4Receiving,SOL_SOCKET,SO_REUSEADDR,&yes,sizeof(yes)) < 0) { 
            cerr << "Problems: Reusing ADDR failed" << endl; 
            exit(1); 
        } 
        // Set up destination address. 
        memset(&addr,0,sizeof(addr)); 
        addr.sin_family=AF_INET; 
        addr.sin_addr.s_addr=htonl(INADDR_ANY); /* N.B.: differs from sender */ 
        addr.sin_port=htons(MDNS_PORT);
       ....

and the last

mDNSQueryWrapper::mDNSQueryWrapper(mNameServer* c): client(c) { 
        // Setup the mDNSClient multicast socket. Something similar to an UDP standard socket. 
        // Once configured, you only need to call queryWrapper->send(string str) method. 
        if ((fd4Sending=socket(AF_INET,SOCK_DGRAM,0)) < 0) { 
            cerr << "Problems creating sending multicast socket" << endl; 
            exit(1); 
        } 
        // Set up multicast group destination address for sending. (It's the same than UDP datagram sending, with an special destination address.) 
        memset(&addr,0,sizeof(addr)); 
        addr.sin_family=AF_INET; 
        addr.sin_addr.s_addr=inet_addr(MDNS_GROUP); 
        addr.sin_port=htons(MDNS_PORT); 
    }

---

### Post by baseface on 2009-09-09
use code tags.
and where are the error messages?

---

### Post by ricky845 on 2009-09-09
Ok.solved. thanks, but sorry for wasting your time because it was string.h missing lib hehe

it doens't hours... hehe

thxs

---

