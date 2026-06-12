---
title: "Difficulty installing app from source"
date: 2009-10-02
forum: General Help
---

### Post by harky on 2009-10-02
I am having problems trying to install some software from source (msgbus-0.1). When trying to "make" the application, it errors claiming that Python.h and structmember.h cannot be found. This problem is reported in many places but the solution always seems to be that you need to install the dev package for python - python2.5-dev in this case. The problem is that the python2.5-dev IS installed. I need help on this one badly. 
 
Please see error output below:
 
>  
$ make
make all-recursive
make[1]: Entering directory `/home/dharkness/msgbus-0.1'
Making all in chatdemo
make[2]: Entering directory `/home/dharkness/msgbus-0.1/chatdemo'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dharkness/msgbus-0.1/chatdemo'
Making all in src
make[2]: Entering directory `/home/dharkness/msgbus-0.1/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dharkness/msgbus-0.1/src'
Making all in python
make[2]: Entering directory `/home/dharkness/msgbus-0.1/python'
/usr/bin/python setup.py build
running build
running build_ext
building 'evmsg' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I.. -I../src -I -I/usr/include/python2.5 -c evmsg.c -o build/temp.linux-x86_64-2.5/evmsg.o
evmsg.c:4:20: error: Python.h: No such file or directory
evmsg.c:5:26: error: structmember.h: No such file or directory

 
And to verify that the python2.5 and the dev package are installed see the output from aptitude:
> $ aptitude search python2.5
p idle-python2.5 - An IDE for Python (v2.5) using Tkinter
v libapache2-mod-python2.5 -
i python2.5 - An interactive high-level object-oriented
 
$ aptitude search python2.5-dev
i A python2.5-dev - Header files and a static library for Pyth
 
Finally, to verify that the files are actually in /usr/include/python2.5 (which is one of the include parameters on the gcc command called by make):
> $ ls -l /usr/include/python2.5/
total 584
.
.
.
-rw-r--r-- 1 root root 4204 2009-07-22 11:53 Python.h
.
.
.
-rw-r--r-- 1 root root 2532 2009-07-22 11:53 structmember.h
.
.
.

 
Any help would be greatly appreciated as I cannot find anything other than "you need to install the python dev package" as a solution. And that has already been done here.
 
Thank You in advance for your help.

---

### Post by Bachstelze on 2009-10-02
You need python2.5-dev.

---

### Post by harky on 2009-10-02
> **Bachstelze said:**
> You need python2.5-dev.
 
If my post does not show that it is properly installed ALREADY please tell me what is wrong with it.  
 
Thank You

---

### Post by Bachstelze on 2009-10-02
Sorry, missed that. ^^; Well, if the compiler doesn't find them, it's probably a bug in the program. Paste the contents of evmsc.c.

---

### Post by harky on 2009-10-02
Nobody else has reported a similar bug, but I have posted it as a bug to the developer as well. In the meantime, here is the code:
 
```
$ cat src/evmsg.c
/* $Id: evmsg.c 118 2008-03-08 03:12:20Z jon.oberheide $ */
#include <sys/types.h>
#include <sys/time.h>
#include <sys/queue.h>
/* XXX - b64_ntop */
#include <netinet/in.h>
#include <arpa/nameser.h>
#include <resolv.h>
#include <assert.h>
#include <event.h>
#include <evhttp.h>
#include <stdlib.h>
#include <string.h>
#include "evmsg.h"
struct evmsg_conn {
        struct evmsg_ctx         *ctx;
        struct event              ev;
        struct timeval            tv;
        struct evhttp_connection *evcon;
        char                     *channel;
        struct evbuffer          *uri;
        evmsg_subscribe_cb        cb;
        void                     *arg;
        char                     *boundary;
        TAILQ_ENTRY(evmsg_conn)   next;
};
struct evmsg_ctx {
        TAILQ_HEAD(, evmsg_conn)  conns;
        char                     *server;
        u_short                   port;
        int                       use_ssl;
        char                     *auth;
} *static_ctx;
static void
__publish_cb(struct evhttp_request *req, void *arg)
{
        if (req == NULL) {
                fprintf(stderr, "NULL req - evhttp_connection_fail?\n");
                return;
        } else if (req->response_code >= 300) {
                fprintf(stderr, "%d: %s\n", req->response_code,
                    req->response_code_line);
                return;
        }
}
static void
__null_cb(struct evhttp_request *req, void *arg)
{
}
static void
__subscribe_cb(struct evhttp_request *req, void *arg)
{
        struct evmsg_conn *conn = arg;
        struct evbuffer *msg, *buf = req->input_buffer;
        struct evkeyvalq kv[1];
        char *p;
        if (conn->cb == NULL) {
                return;
        } else if (req == NULL) {
                fprintf(stderr, "NULL req - evhttp_connection_fail?\n");
                return;
        } else if (req->evcon == NULL) {
                fprintf(stderr, "NULL evcon - evhttp_connection_done?\n");
                return;
        } else if (req->response_code >= 300) {
                fprintf(stderr, "%d: %s\n", req->response_code,
                    req->response_code_line);
                return;
        }
        /* Parse the multipart boundary, once. */
        if (conn->boundary == NULL) {
                const char *t = evhttp_find_header(req->input_headers,
                    "Content-Type");
                /* XXX - multipart/x-mixed-replace;boundary=00MsgBus00 */
                t = strchr(t, '=') + 1;
                conn->boundary = malloc(2 + strlen(t) + 1);
                sprintf(conn->boundary, "--%s", t);
        }
        /* Parse buffer for internal hdrs */
        TAILQ_INIT(kv);
        while ((p = evbuffer_readline(buf)) != NULL && p[0] != '\0') {
                char *k = strsep(&p, ":");
                if (p != NULL &&
                    (strcasecmp(k, "Content-Type") == 0 ||
                        strcasecmp(k, "From") == 0 ||
                        strcasecmp(k, "Content-Location") == 0)) {
                        p += strspn(p, " ");
                        evhttp_add_header(kv, k, p);
                }
                free(k);
        }
        /*
         * XXX - assume msgbus' chunks correspond to multipart
         * boundaries (too chummy with the server implementation?)
         */
        if ((p = (char *)evbuffer_find(buf, (u_char *)conn->boundary,
                 strlen(conn->boundary))) != NULL &&
            evhttp_find_header(kv, "Content-Type") != NULL) {
                int n = (u_char *)p - EVBUFFER_DATA(buf);
                msg = evbuffer_new();
                evbuffer_add(msg, EVBUFFER_DATA(buf), n);
                evbuffer_expand(msg, n + 1);
                EVBUFFER_DATA(msg)[n] = '\0';
                p = conn->channel;
                if (*p == '\0') {
                        p = (char *)evhttp_find_header(kv, "Content-Location");
                        if (strncmp(p, "/msgbus/", 8) == 0)
                                p += 8;
                }
                (*conn->cb)(p ? p : "", evhttp_find_header(kv, "Content-Type"),
                    evhttp_find_header(kv, "From"), msg, conn->arg);
                evbuffer_free(msg);
        }
        evhttp_clear_headers(kv);
}
static void
__subscribe_open(struct evhttp_connection *evcon, void *arg)
{
        struct evmsg_conn *conn = arg;
        struct evmsg_ctx *ctx = conn->ctx;
        struct evhttp_request *req;
#ifdef HAVE_OPENSSL
        if (ctx->use_ssl) {
                conn->evcon = evhttp_connection_new_ssl(ctx->server,
                    ctx->port);
        } else
#endif
        {
                conn->evcon = evhttp_connection_new(ctx->server, ctx->port);
        }
        evhttp_connection_set_timeout(conn->evcon, 0);
        evhttp_connection_set_retries(conn->evcon, -1);
        evhttp_connection_set_closecb(conn->evcon, __subscribe_open, conn);
        req = evhttp_request_new(__null_cb, conn);
        evhttp_request_set_chunked_cb(req, __subscribe_cb);
        evhttp_add_header(req->output_headers, "Host", ctx->server);
        evhttp_add_header(req->output_headers, "User-Agent", "libevmsg");
        if (ctx->auth != NULL) {
                evhttp_add_header(req->output_headers, "Authorization",
                    ctx->auth);
        }
        evhttp_make_request(conn->evcon, req, EVHTTP_REQ_GET,
            (char *)EVBUFFER_DATA(conn->uri));
}
static void
__uri_escape(struct evbuffer *buf)
{
        char *p;
        evbuffer_add(buf, "", 1);
        p = evhttp_encode_uri((char *)EVBUFFER_DATA(buf));
        evbuffer_drain(buf, EVBUFFER_LENGTH(buf));
        evbuffer_add_printf(buf, "%s", p);
        evbuffer_add(buf, "", 1);
        free(p);
}
struct evmsg_ctx *
evmsg_ctx_open(const char *server, u_short port, int use_ssl)
{
        struct evmsg_ctx *ctx = calloc(1, sizeof(*ctx));
        struct evmsg_conn *conn;
        if (server == NULL)
                server = "127.0.0.1";
        if (port == 0)
                port = use_ssl ? EVMSG_DEFAULT_SSL_PORT : EVMSG_DEFAULT_PORT;
        ctx->server = strdup(server);
        ctx->port = port;
        ctx->use_ssl = use_ssl;
        /* First connection is for publishing */
        TAILQ_INIT(&ctx->conns);
        conn = calloc(1, sizeof(*conn));
        conn->ctx = ctx;
        conn->uri = evbuffer_new();
        if (ctx->use_ssl) {
#ifdef HAVE_OPENSSL
                conn->evcon = evhttp_connection_new_ssl(ctx->server,
                    ctx->port);
#else
                evmsg_ctx_close(&ctx);
                return (ctx);
#endif
        } else {
                conn->evcon = evhttp_connection_new(ctx->server, ctx->port);
        }
        evhttp_connection_set_retries(conn->evcon, -1);
        TAILQ_INSERT_HEAD(&ctx->conns, conn, next);
        return (ctx);
}
void
evmsg_open(const char *server, u_short port, int use_ssl)
{
        static_ctx = evmsg_ctx_open(server, port, use_ssl);
}
void
evmsg_ctx_set_auth(struct evmsg_ctx *ctx,
    const char *username, const char *password)
{
        struct evbuffer *tmp = evbuffer_new();
        int len;
        assert(username != NULL && password != NULL);
        free(ctx->auth);
        len = evbuffer_add_printf(tmp, "%s:%s", username, password);
        ctx->auth = malloc(6 + len * 2);
        strcpy(ctx->auth, "Basic ");
        b64_ntop(EVBUFFER_DATA(tmp), len, ctx->auth + 6, len * 2);
        evbuffer_free(tmp);
}
void
evmsg_set_auth(const char *username, const char *password)
{
        evmsg_ctx_set_auth(static_ctx, username, password);
}
int
evmsg_ctx_publish(struct evmsg_ctx *ctx,
    const char *channel, const char *type, struct evbuffer *msg)
{
        static char *buf;
        static int len;
        struct evmsg_conn *conn = TAILQ_FIRST(&ctx->conns);
        struct evhttp_request *req;
        int n = strlen(channel);
        if (len < n + 1) {
                len = 10 + n;
                free(buf);
                buf = malloc(len);
        }
        req = evhttp_request_new(__publish_cb, NULL);
        evhttp_add_header(req->output_headers, "Host", ctx->server);
        evhttp_add_header(req->output_headers, "User-Agent", "libevmsg");
        if (ctx->auth != NULL) {
                evhttp_add_header(req->output_headers, "Authorization",
                    ctx->auth);
        }
        evhttp_add_header(req->output_headers, "Content-Type", type);
        evbuffer_add_buffer(req->output_buffer, msg);
        evbuffer_drain(conn->uri, EVBUFFER_LENGTH(conn->uri));
        evbuffer_add_printf(conn->uri, "/msgbus/%s", channel);
        __uri_escape(conn->uri);
        return (evhttp_make_request(conn->evcon, req, EVHTTP_REQ_POST,
                    (char *)EVBUFFER_DATA(conn->uri)));
}
int
evmsg_publish(const char *channel, const char *type, struct evbuffer *msg)
{
        return (evmsg_ctx_publish(static_ctx, channel, type, msg));
}
void *
evmsg_ctx_subscribe(struct evmsg_ctx *ctx,
    const char *channel, const char *type, const char *sender,
    void (*callback)(const char *channel, const char *type, const char *sender,
        struct evbuffer *buf, void *arg), void *arg)
{
        char *qs;
        struct evmsg_conn *conn;
        conn = calloc(1, sizeof(*conn));
        conn->ctx = ctx;
        conn->uri = evbuffer_new();
        conn->cb = callback;
        conn->arg = arg;
        if (channel == NULL || strcmp(channel, "*") == 0)
                channel = "";
        conn->channel = strdup(channel);
        qs = evhttp_encode_uri(channel);
        evbuffer_add_printf(conn->uri, "/msgbus/%s?", qs);
        free(qs);
        qs = evhttp_encode_uri(type ? type : "*");
        evbuffer_add_printf(conn->uri, "type=%s&", qs);
        free(qs);
        qs = evhttp_encode_uri(sender ? sender : "*");
        evbuffer_add_printf(conn->uri, "sender=%s", qs);
        free(qs);
        TAILQ_INSERT_TAIL(&ctx->conns, conn, next);
        __subscribe_open(NULL, conn);
        return ((void *)conn);
}
void *
evmsg_subscribe(const char *channel, const char *type, const char *sender,
    void (*callback)(const char *channel, const char *type, const char *sender,
        struct evbuffer *buf, void *arg), void *arg)
{
        return (evmsg_ctx_subscribe(static_ctx,
                    channel, type, sender, callback, arg));
}
void
evmsg_ctx_unsubscribe(struct evmsg_ctx *ctx, void *arg)
{
        struct evmsg_conn *conn = arg;
        TAILQ_REMOVE(&ctx->conns, conn, next);
        evhttp_connection_set_closecb(conn->evcon, NULL, NULL);
        evhttp_connection_free(conn->evcon);
        if (conn->uri != NULL)
                evbuffer_free(conn->uri);
        free(conn->channel);
        free(conn);
}
void
evmsg_unsubscribe(void *arg)
{
        evmsg_ctx_unsubscribe(static_ctx, arg);
}
void
evmsg_ctx_close(struct evmsg_ctx **ctx)
{
        struct evmsg_conn *conn;
        /* Shutdown all our connections. */
        while ((conn = TAILQ_FIRST(&ctx[0]->conns)) != NULL) {
                evmsg_ctx_unsubscribe(ctx[0], conn);
        }
        free(ctx[0]->auth);
        free(ctx[0]->server);
        free(ctx[0]);
        ctx[0] = NULL;
}
void
evmsg_close(void)
{
        evmsg_ctx_close(&static_ctx);
}
```

---

### Post by Bachstelze on 2009-10-02
Hmm, no mention of Python.h here. Maybe in evmsg.h?

---

### Post by harky on 2009-10-02
I grepped the entire source directory (of the application I am trying to compile) for python and this is what I came up with:
 
```
$ grep Python.h ./*
$ grep Python ./*
$ grep python ./*
./Makefile:PYTHON = /usr/bin/python
./Makefile:pkgpythondir = ${pythondir}/msgbus
./Makefile:pyexecdir = ${exec_prefix}/lib/python2.5/site-packages
./Makefile:pythondir = ${prefix}/lib/python2.5/site-packages
./Makefile.in:pkgpythondir = @pkgpythondir@
./Makefile.in:pythondir = @pythondir@

```

---

### Post by Bachstelze on 2009-10-02
The file that tries to include Python.h is python/evmsg.c:

```
firas@iori msgbus-0.1 % grep -ir Python.h .
./python/evmsg.pyx:cdef extern from "Python.h":
./python/evmsg.c:#include "Python.h"

```

Compile with

```
make CFLAGS=-I/usr/include/python2.5/
```

and it works.

---

### Post by harky on 2009-10-02
Thank you very much for your help.  That seems to have fixed it.  I will report that to the developer.

---

