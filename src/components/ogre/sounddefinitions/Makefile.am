INCLUDES = -I$(top_srcdir)/src
METASOURCES = AUTO
current = $(PWD)

dist-hook:
	mkdir -p $(distdir)
	(cd $(top_srcdir)/src/components/ogre/sounddefinitions && tar cf - `find . -name \*.sounddef` | ( cd $(current) && cd $(distdir) && tar xf -))
# 	(cd $(top_srcdir)/src/components/ogre/sounddefinitions && tar cf - `find . -name \*.sounddef.xml` | ( cd $(current) && cd $(distdir) && tar xf -))

install-data-local:
	mkdir -p $(DESTDIR)$(datadir)/ember/media/shared/sounddefinitions 

uninstall-local:
	find $(DESTDIR)$(datadir)/ember/media/shared/sounddefinitions -name  \*.sounddef | xargs rm -f
# 	find $(DESTDIR)$(datadir)/ember/media/shared/sounddefinitions -name  \*.sounddef.xml | xargs rm -f

check-local:
	@set -e; for rule in `find $(top_srcdir)/src/components/ogre/sounddefinitions \*.sounddef -or -name \*.sounddef.xml` ; do \
		echo $(XMLLINT) -noout $$rule; \
		$(XMLLINT) -noout $$rule; \
	done;
