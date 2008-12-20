# $Id: makefile.in,v 1.8 2005/07/25 19:56:26 tom Exp $
# Makefile-template for 'bcpp'

THIS		= bcpp

#### Start of system configuration section. ####

srcdir		= .


CXX		= g++
CXXFLAGS	= -g -O2
EXTRA_CXXFLAGS	= -W -Wall -Wabi -fabi-version=0 -Woverloaded-virtual -Wsign-promo -Wsynth -Wold-style-cast -Wcast-align -Wcast-qual -Wpointer-arith -Wshadow -Wundef -Weffc++

INSTALL		= /usr/bin/install -c
INSTALL_PROGRAM	= ${INSTALL}
INSTALL_DATA	= ${INSTALL} -m 644

LINK		= $(CXX)
LIBS		= 
LDFLAGS		= 

prefix		= /usr/local
exec_prefix	= ${prefix}

bindir		= $(DESTDIR)${exec_prefix}/bin

x		= 
o		= .o

#### End of system configuration section. ####

SHELL		= /bin/sh

OBJS	= \
	bcpp$o \
	anyobj$o \
	backup$o \
	baseq$o \
	cmdline$o \
	config$o \
	debug$o \
	execsql$o \
	hanging$o \
	html$o \
	stacklis$o \
	strings$o \
	tabs$o \
	verbose$o

CPPFLAGS	= -I. -I$(srcdir) \
		-DVERSION=\"`cat $(srcdir)/../VERSION`\" \
		-DHAVE_CONFIG_H # -DDEBUG -DDEBUG2

PROG	= $(THIS)$x

.SUFFIXES: .cpp $o

.cpp$o:
# compiling
	$(CXX) $(CXXFLAGS) $(EXTRA_CXXFLAGS) $(CPPFLAGS) -c $< -o $@

all:	$(PROG)

$(PROG): $(OBJS)
	$(LINK) $(LDFLAGS) -o $(PROG) $(OBJS) $(LIBS)

install: all installdirs
	$(INSTALL_PROGRAM) $(PROG) $(bindir)/$(PROG)

installdirs:
	$(SHELL) ${srcdir}/../mkdirs.sh $(bindir)

uninstall:
	rm -f $(bindir)/$(PROG)

mostlyclean:
	rm -f *$o core *~ *.out *.BAK *.atac

clean: mostlyclean
	rm -f $(PROG)

distclean: clean
	rm -f makefile config.log config.cache config.status autoconf.h

realclean: distclean
	rm -f tags TAGS # don't remove configure!

check:
	$(SHELL) ./run-test

tags:
	ctags *.cpp *.h

TAGS:
	etags *.cpp *.h

$(OBJS):	autoconf.h bcpp.h
