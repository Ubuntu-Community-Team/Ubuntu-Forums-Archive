---
title: "Qt errors when trying to install last.fm scrobbler"
date: 2011-06-15
forum: General Help
---

### Post by starrtennis on 2011-06-15
I have Ubuntue 10.04.2 installed. I used apt-get to install the package that includes qmake (qt-qmake? whatever it's called, I forget), which appears necessary to install the last.fm scrobbler.

So, the configure runs smoothly. But then when I make, there are tons of errors:

> mike@Lilly:~/src/last.fm-1.4.2.58240$ make
In file included from CachedHttp.cpp:23:
CachedHttp.h:28:18: error: QDebug: No such file or directory
CachedHttp.h:29:17: error: QHttp: No such file or directory
CachedHttp.h:30:17: error: QHash: No such file or directory
CachedHttp.h:31:18: error: QStack: No such file or directory
CachedHttp.h:32:19: error: QString: No such file or directory
In file included from Settings.h:26,
                 from CachedHttp.cpp:24:
UnicornCommon.h:28:19: error: QLocale: No such file or directory
In file included from CachedHttp.cpp:24:
Settings.h:29:16: error: QMap: No such file or directory
Settings.h:30:18: error: QPoint: No such file or directory
Settings.h:31:21: error: QSettings: No such file or directory
Settings.h:32:17: error: QSize: No such file or directory
Settings.h:33:23: error: QStringList: No such file or directory
Settings.h:34:18: error: QMutex: No such file or directory
Settings.h:35:24: error: QMutexLocker: No such file or directory
Settings.h:36:28: error: QCoreApplication: No such file or directory
In file included from CachedHttp.cpp:25:
WebService.h:26:24: error: QApplication: No such file or directory
WebService.h:27:16: error: QUrl: No such file or directory
WebService.h:28:21: error: QDateTime: No such file or directory
In file included from WebService.h:31,
                 from CachedHttp.cpp:25:
Track.h:30:20: error: QVariant: No such file or directory
CachedHttp.cpp:27:16: error: QDir: No such file or directory
CachedHttp.cpp:28:18: error: QTimer: No such file or directory
In file included from CachedHttp.h:34,
                 from CachedHttp.cpp:23:
RedirectHttp.h:34: error: expected class-name before ‘{’ token
RedirectHttp.h:35: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
RedirectHttp.h:37: error: expected ‘;’ before ‘public’
RedirectHttp.h:42: error: ISO C++ forbids declaration of ‘QString’ with no type
RedirectHttp.h:42: error: expected ‘,’ or ‘...’ before ‘&’ token
RedirectHttp.h:43: error: ISO C++ forbids declaration of ‘QString’ with no type
RedirectHttp.h:43: error: expected ‘,’ or ‘...’ before ‘&’ token
RedirectHttp.h:44: error: ISO C++ forbids declaration of ‘QString’ with no type
RedirectHttp.h:44: error: expected ‘,’ or ‘...’ before ‘&’ token
RedirectHttp.h:44: error: ‘int RedirectHttp::post(int)’ cannot be overloaded
RedirectHttp.h:43: error: with ‘int RedirectHttp::post(int)’
RedirectHttp.h:45: error: ISO C++ forbids declaration of ‘QHttpRequestHeader’ with no type
RedirectHttp.h:45: error: expected ‘,’ or ‘...’ before ‘&’ token
RedirectHttp.h:46: error: ISO C++ forbids declaration of ‘QHttpRequestHeader’ with no type
RedirectHttp.h:46: error: expected ‘,’ or ‘...’ before ‘&’ token
RedirectHttp.h:46: error: ‘int RedirectHttp::request(int)’ cannot be overloaded
RedirectHttp.h:45: error: with ‘int RedirectHttp::request(int)’
RedirectHttp.h:48: error: expected ‘:’ before ‘slots’
RedirectHttp.h:49: error: expected primary-expression before ‘void’
RedirectHttp.h:49: error: ISO C++ forbids declaration of ‘slots’ with no type
RedirectHttp.h:49: error: expected ‘;’ before ‘void’
RedirectHttp.h:65: error: ‘QByteArray’ does not name a type
RedirectHttp.h:66: error: ISO C++ forbids declaration of ‘QIODevice’ with no type
RedirectHttp.h:66: error: expected ‘;’ before ‘*’ token
RedirectHttp.h:67: error: ISO C++ forbids declaration of ‘QIODevice’ with no type
RedirectHttp.h:67: error: expected ‘;’ before ‘*’ token
RedirectHttp.h:68: error: ‘QHttpRequestHeader’ does not name a type
RedirectHttp.h:70: error: ISO C++ forbids declaration of ‘QHash’ with no type
RedirectHttp.h:70: error: expected ‘;’ before ‘<’ token
In file included from CachedHttp.cpp:23:
CachedHttp.h:38: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
CachedHttp.h:40: error: expected ‘;’ before ‘public’
CachedHttp.h:49: error: expected ‘)’ before ‘*’ token
CachedHttp.h:50: error: ISO C++ forbids declaration of ‘QString’ with no type
CachedHttp.h:50: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:53: error: ISO C++ forbids declaration of ‘QString’ with no type
CachedHttp.h:53: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:54: error: ISO C++ forbids declaration of ‘QString’ with no type
CachedHttp.h:54: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:54: error: ‘int CachedHttp::get(int)’ cannot be overloaded
CachedHttp.h:53: error: with ‘int CachedHttp::get(int)’
CachedHttp.h:55: error: ISO C++ forbids declaration of ‘QString’ with no type
CachedHttp.h:55: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:56: error: ISO C++ forbids declaration of ‘QString’ with no type
CachedHttp.h:56: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:56: error: ‘int CachedHttp::post(int)’ cannot be overloaded
CachedHttp.h:55: error: with ‘int CachedHttp::post(int)’
CachedHttp.h:57: error: ISO C++ forbids declaration of ‘QHttpRequestHeader’ with no type
CachedHttp.h:57: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:58: error: ISO C++ forbids declaration of ‘QHttpRequestHeader’ with no type
CachedHttp.h:58: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:58: error: ‘int CachedHttp::request(int)’ cannot be overloaded
CachedHttp.h:57: error: with ‘int CachedHttp::request(int)’
CachedHttp.h:60: error: ISO C++ forbids declaration of ‘QString’ with no type
CachedHttp.h:60: error: expected ‘,’ or ‘...’ before ‘&’ token
In file included from CachedHttp.cpp:23:
CachedHttp.h:61: error: ‘QByteArray’ does not name a type
CachedHttp.h:63: error: ‘qint64’ does not name a type
CachedHttp.h:65: error: ‘QString’ does not name a type
CachedHttp.h:70: error: ‘QString’ has not been declared
CachedHttp.h:71: error: ‘QString’ has not been declared
CachedHttp.h:73: error: expected ‘:’ before ‘slots’
CachedHttp.h:74: error: expected primary-expression before ‘void’
CachedHttp.h:74: error: ISO C++ forbids declaration of ‘slots’ with no type
CachedHttp.h:74: error: expected ‘;’ before ‘void’
CachedHttp.h:77: error: expected primary-expression before ‘void’
CachedHttp.h:77: error: ISO C++ forbids declaration of ‘signals’ with no type
CachedHttp.h:77: error: expected ‘;’ before ‘void’
CachedHttp.h:78: error: ISO C++ forbids declaration of ‘QByteArray’ with no type
CachedHttp.h:78: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:80: error: expected ‘:’ before ‘slots’
CachedHttp.h:81: error: expected primary-expression before ‘void’
CachedHttp.h:81: error: ISO C++ forbids declaration of ‘slots’ with no type
CachedHttp.h:81: error: expected ‘;’ before ‘void’
CachedHttp.h:83: error: ISO C++ forbids declaration of ‘QHttpResponseHeader’ with no type
CachedHttp.h:83: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:91: error: ‘QString’ does not name a type
CachedHttp.h:97: error: ‘QString’ has not been declared
CachedHttp.h:104: error: ‘QByteArray’ does not name a type
CachedHttp.h:105: error: ‘QString’ does not name a type
CachedHttp.h:109: error: ‘ProxyOverrideState’ does not name a type
CachedHttp.h:112: error: ISO C++ forbids declaration of ‘QHash’ with no type
CachedHttp.h:112: error: expected ‘;’ before ‘<’ token
CachedHttp.h:113: error: ISO C++ forbids declaration of ‘QStack’ with no type
CachedHttp.h:113: error: expected ‘;’ before ‘<’ token
CachedHttp.h:118: error: ‘QHttpRequestHeader’ has not been declared
CachedHttp.h:121: error: ‘QString’ does not name a type
CachedHttp.h:122: error: ‘QString’ does not name a type
CachedHttp.h:124: error: ‘QString’ does not name a type
CachedHttp.h:125: error: ‘QString’ has not been declared
CachedHttp.h:126: error: ‘QString’ has not been declared
CachedHttp.h:126: error: ISO C++ forbids declaration of ‘QByteArray’ with no type
CachedHttp.h:126: error: expected ‘,’ or ‘...’ before ‘&’ token
CachedHttp.h:130: error: ‘QString’ does not name a type
CachedHttp.h:131: error: ‘QString’ does not name a type
In file included from CachedHttp.cpp:23:
CachedHttp.h: In member function ‘int CachedHttp::setHost(int)’:
CachedHttp.h:60: error: ‘m_hostname’ was not declared in this scope
CachedHttp.h:60: error: ‘hostName’ was not declared in this scope
CachedHttp.h:60: error: ‘QHttp’ has not been declared
CachedHttp.h:60: error: ‘port’ was not declared in this scope
In file included from CachedHttp.cpp:23:
CachedHttp.h: In static member function ‘static void CachedHttp::setCustomUserAgent(int)’:
CachedHttp.h:70: error: ‘s_customUserAgent’ was not declared in this scope
CachedHttp.h: In static member function ‘static void CachedHttp::setCustomCachePath(int)’:
CachedHttp.h:71: error: ‘s_customCachePath’ was not declared in this scope
CachedHttp.h: In constructor ‘CachedHttp::CachedRequestData::CachedRequestData(int, int)’:
CachedHttp.h:99: error: class ‘CachedHttp::CachedRequestData’ does not have any field named ‘m_cacheKey’
CachedHttp.h: In member function ‘void CachedHttp::checkBuffer()’:
CachedHttp.h:119: error: ‘QHttp’ has not been declared
CachedHttp.h:119: error: ‘m_buffer’ was not declared in this scope
CachedHttp.h:119: error: ‘QHttp’ has not been declared
CachedHttp.h: At global scope:
CachedHttp.h:135: error: expected initializer before ‘operator’
In file included from Settings.h:26,
                 from CachedHttp.cpp:24:
UnicornCommon.h:78: error: ‘QString’ does not name a type
UnicornCommon.h:85: error: ‘QString’ does not name a type
UnicornCommon.h:91: error: ‘QString’ does not name a type
UnicornCommon.h:98: error: ‘QString’ does not name a type
UnicornCommon.h:104: error: ‘QString’ does not name a type
UnicornCommon.h:139: error: variable or field ‘stripBBCode’ declared void
UnicornCommon.h:139: error: ‘QString’ was not declared in this scope
UnicornCommon.h:139: error: ‘str’ was not declared in this scope
UnicornCommon.h:151: error: ‘QString’ does not name a type
UnicornCommon.h:165: error: expected constructor, destructor, or type conversion before ‘&’ token
UnicornCommon.h:171: error: ‘QStringList’ does not name a type
UnicornCommon.h:183: error: ‘QString’ does not name a type
UnicornCommon.h:186: error: ‘QString’ does not name a type
In file included from Settings.h:27,
                 from CachedHttp.cpp:24:
StationUrl.h:29: error: expected class-name before ‘{’ token
StationUrl.h:32: error: ISO C++ forbids declaration of ‘QString’ with no type
StationUrl.h:32: error: expected ‘,’ or ‘...’ before ‘&’ token
In file included from CachedHttp.cpp:24:
Settings.h:48: error: expected ‘)’ before ‘*’ token
Settings.h:61: error: expected class-name before ‘{’ token
Settings.h:62: error: ‘Q_OBJECT’ does not name a type
Settings.h:73: error: ISO C++ forbids declaration of ‘QString’ with no type
Settings.h:73: error: expected ‘,’ or ‘...’ before ‘&’ token
Settings.h:77: error: ‘QString’ does not name a type
Settings.h:79: error: ‘QString’ does not name a type
Settings.h:80: error: ‘QString’ has not been declared
Settings.h:113: error: ‘QString’ does not name a type
Settings.h: In constructor ‘UserSettings<T>::UserSettings(int)’:
Settings.h:73: error: class ‘UserSettings<T>’ does not have any field named ‘m_username’
Settings.h:73: error: ‘username’ was not declared in this scope
Settings.h: In member function ‘bool UserSettings<T>::isNull() const’:
Settings.h:75: error: ‘m_username’ was not declared in this scope
Settings.h: In member function ‘void UserSettings<T>::setPassword(int)’:
Settings.h:82: error: request for member ‘isEmpty’ in ‘password’, which is of non-class type ‘int’
Settings.h:82: error: ISO C++ forbids comparison between pointer and integer
Settings.h:84: error: ‘md5Digest’ is not a member of ‘UnicornUtils’
Settings.h:84: error: request for member ‘toUtf8’ in ‘password’, which is of non-class type ‘int’
Settings.h:86: error: ‘emit’ was not declared in this scope
Settings.h:86: error: expected ‘;’ before ‘userChanged’
Settings.h: In member function ‘void UserSettings<T>::setRememberPass(bool)’:
Settings.h:99: error: ‘emit’ was not declared in this scope
Settings.h:99: error: expected ‘;’ before ‘userChanged’
Settings.h: At global scope:
Settings.h:123: error: expected class-name before ‘{’ token
In file included from CachedHttp.cpp:24:
Settings.h:128: error: expected ‘)’ before ‘*’ token
Settings.h:133: error: ‘QString’ does not name a type
Settings.h:134: error: ‘QString’ has not been declared
Settings.h:139: error: ‘QString’ does not name a type
Settings.h:140: error: ‘QString’ has not been declared
Settings.h:142: error: ‘QString’ does not name a type
Settings.h:143: error: ‘QString’ has not been declared
Settings.h: In member function ‘bool SharedSettings::isUseProxy() const’:
Settings.h:130: error: ‘QCoreApplication’ has not been declared
Settings.h:130: error: ‘QCoreApplication’ has not been declared
Settings.h:130: error: ‘QSettings’ was not declared in this scope
Settings.h: In member function ‘void SharedSettings::setUseProxy(bool)’:
Settings.h:131: error: ‘QCoreApplication’ has not been declared
Settings.h:131: error: ‘QCoreApplication’ has not been declared
Settings.h:131: error: ‘QSettings’ was not declared in this scope
Settings.h: In member function ‘void SharedSettings::setProxyHost(int)’:
Settings.h:134: error: ‘QCoreApplication’ has not been declared
Settings.h:134: error: ‘QCoreApplication’ has not been declared
Settings.h:134: error: ‘QSettings’ was not declared in this scope
Settings.h: In member function ‘int SharedSettings::getProxyPort() const’:
Settings.h:136: error: ‘QCoreApplication’ has not been declared
Settings.h:136: error: ‘QCoreApplication’ has not been declared
Settings.h:136: error: ‘QSettings’ was not declared in this scope
Settings.h: In member function ‘void SharedSettings::setProxyPort(int)’:
Settings.h:137: error: ‘QCoreApplication’ has not been declared
Settings.h:137: error: ‘QCoreApplication’ has not been declared
Settings.h:137: error: ‘QSettings’ was not declared in this scope
Settings.h: In member function ‘void SharedSettings::setProxyUser(int)’:
Settings.h:140: error: ‘QCoreApplication’ has not been declared
Settings.h:140: error: ‘QCoreApplication’ has not been declared
Settings.h:140: error: ‘QSettings’ was not declared in this scope
Settings.h: In member function ‘void SharedSettings::setProxyPassword(int)’:
Settings.h:143: error: ‘QCoreApplication’ has not been declared
Settings.h:143: error: ‘QCoreApplication’ has not been declared
Settings.h:143: error: ‘QSettings’ was not declared in this scope
Settings.h: In static member function ‘static SharedSettings* SharedSettings::instance()’:
Settings.h:165: error: ‘Q_ASSERT’ was not declared in this scope
Settings.h: At global scope:
Settings.h:191: error: expected ‘)’ before ‘*’ token
Settings.h:193: error: ‘QString’ does not name a type
Settings.h:194: error: ‘QString’ has not been declared
Settings.h:196: error: ‘QString’ does not name a type
Settings.h:201: error: ‘QString’ has not been declared
Settings.h:203: error: ‘QByteArray’ does not name a type
Settings.h:204: error: ‘QByteArray’ has not been declared
Settings.h:206: error: ‘Qt’ has not been declared
Settings.h:206: error: ISO C++ forbids declaration of ‘WindowState’ with no type
Settings.h:206: error: expected ‘;’ before ‘containerWindowState’
Settings.h:207: error: expected ‘;’ before ‘void’
Settings.h:210: error: ‘QString’ does not name a type
Settings.h:228: error: ‘QString’ does not name a type
Settings.h:229: error: ‘QString’ has not been declared
In file included from WebService.h:31,
                 from CachedHttp.cpp:25:
Track.h:40: error: ‘QString’ does not name a type
Track.h:40: error: ‘QString’ does not name a type
Track.h:40: error: ‘QString’ has not been declared
Track.h:41: error: ‘QString’ does not name a type
Track.h:41: error: ‘QString’ does not name a type
Track.h:41: error: ‘QString’ has not been declared
Track.h:42: error: ‘QString’ does not name a type
Track.h:42: error: ‘QString’ does not name a type
Track.h:42: error: ‘QString’ has not been declared
Track.h:52: error: ‘QString’ does not name a type
Track.h:64: error: ‘QString’ does not name a type
Track.h:67: error: expected type-specifier before ‘QString’
Track.h:68: error: expected type-specifier before ‘QVariant’
Track.h: In member function ‘void Track::setArtist(int)’:
Track.h:40: error: ‘m_artist’ was not declared in this scope
Track.h: In member function ‘void Track::setTitle(int)’:
Track.h:41: error: ‘m_title’ was not declared in this scope
Track.h: In member function ‘void Track::setAlbum(int)’:
Track.h:42: error: ‘m_album’ was not declared in this scope
Track.h: In member function ‘bool Track::operator==(const Track&)’:
Track.h:49: error: ‘const class Track’ has no member named ‘m_artist’
Track.h:49: error: ‘m_artist’ was not declared in this scope
Track.h:49: error: ‘m_title’ was not declared in this scope
Track.h:49: error: ‘const class Track’ has no member named ‘m_title’
Track.h: In member function ‘bool Track::isEmpty() const’:
Track.h:73: error: ‘m_title’ was not declared in this scope
Track.h:73: error: ‘m_artist’ was not declared in this scope
In file included from WeightedStringList.h:24,
                 from WebService.h:32,
                 from CachedHttp.cpp:25:
WeightedString.h: At global scope:
WeightedString.h:30: error: expected class-name before ‘{’ token
WeightedString.h:35: error: expected ‘)’ before ‘name’
WeightedString.h:37: error: ‘QString’ has not been declared
WeightedString.h:44: error: ‘QString’ has not been declared
WeightedString.h: In static member function ‘static WeightedString WeightedString::weighted(int, int)’:
WeightedString.h:39: error: no matching function for call to ‘WeightedString::WeightedString(int&)’
WeightedString.h:33: note: candidates are: WeightedString::WeightedString()
WeightedString.h:30: note:                 WeightedString::WeightedString(const WeightedString&)
WeightedString.h: In static member function ‘static WeightedString WeightedString::counted(int, int)’:
WeightedString.h:46: error: no matching function for call to ‘WeightedString::WeightedString(int&)’
WeightedString.h:33: note: candidates are: WeightedString::WeightedString()
WeightedString.h:30: note:                 WeightedString::WeightedString(const WeightedString&)
In file included from WebService.h:32,
                 from CachedHttp.cpp:25:
WeightedStringList.h: At global scope:
WeightedStringList.h:38: error: expected template-name before ‘<’ token
WeightedStringList.h:38: error: expected ‘{’ before ‘<’ token
WeightedStringList.h:38: error: expected unqualified-id before ‘<’ token
make[1]: *** [../../build/LastFmTools/release/CachedHttp.o] Error 1
make: *** [sub-src-libUnicorn-make_default-ordered] Error 2Help?

And sorry if this is posted in the wrong location. I searched the forum for "last.fm" and got no hits.

---

