M1_C=src/m1/m1.c
M2_C=src/m2/m2.c
M1_H=$(addprefix -I, src/m1/include)
M2_H=$(addprefix -I, src/m2/include)
M_H=$(addprefix -I, include)

main: m1.o m2.o
	gcc output/m1.o output/m2.o -o output/main

m1.o: m1.s
	gcc -c output/m1.s -o output/m1.o

m2.o: m2.s
	gcc -c output/m2.s -o output/m2.o

m1.s: $(M1_C)
	gcc -S $(M_H) $(M1_H) $(M2_H) $(M1_C) -o output/m1.s

m2.s: $(M2_C)
	gcc -S $(M_H) $(M1_H) $(M2_H) $(M2_C) -o output/m2.s

all: main

install: main
	install main /usr/local/bin/

install-strip: main
	install -s main /usr/local/bin/

uninstall:
	rm -rf /usr/local/bin/main

clean:
	rm -rf output/*

.PHONY: clean

