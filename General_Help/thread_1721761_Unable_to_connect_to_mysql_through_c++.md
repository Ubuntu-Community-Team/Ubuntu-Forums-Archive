---
title: "Unable to connect to mysql through c++"
date: 2011-04-04
forum: General Help
---

### Post by testacc753 on 2011-04-04
Whenever i build a c++ project with mysql connectivity i get these errors..

g++     -o dist/Debug/GNU-Linux-x86/mysqltest build/Debug/GNU-Linux-x86/main.o -L/usr/local/lib/lib -L/usr/lib -lmysqlcppconn -lmysqlclient 
make[2]: Leaving directory `/home/prasanth/NetBeansProjects/mysqltest'
make[1]: Leaving directory `/home/prasanth/NetBeansProjects/mysqltest'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `vtable for std::basic_streambuf<char, std::char_traits<char> >@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_ios<char, std::char_traits<char> >::~basic_ios()@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::ios_base::ios_base()@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_ios<char, std::char_traits<char> >::init(std::basic_streambuf<char, std::char_traits<char> >*)@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >::str() const@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::compare(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) const@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `vtable for std::bad_alloc@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `__gxx_personality_v0@CXXABI_1.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(long)@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::ios_base::~ios_base()@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::bad_alloc::~bad_alloc()@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_streambuf<char, std::char_traits<char> >::~basic_streambuf()@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::ios_base::Init::~Init()@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `vtable for std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::assign(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::__throw_logic_error(char const*)@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(unsigned long)@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, unsigned int, std::allocator<char> const&)@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `std::basic_streambuf<char, std::char_traits<char> >::basic_streambuf()@GLIBCPP_3.2'
/usr/local/lib/lib/libmysqlcppconn.so: undefined reference to `typeinfo for std::bad_alloc@GLIBCPP_3.2'

---

