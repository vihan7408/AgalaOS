# AGAS Kernel Build Configuration

CC = gcc
AS = nasm
LD = ld
CFLAGS = -ffreestanding -fno-stack-protector -fno-builtin -Wall -Wextra -m64
ASFLAGS = -f elf64
LDFLAGS = -T linker.ld -m elf_x86_64

TARGET = agas_kernel.elf

SOURCES = agas_kernel.c
OBJECTS = $(SOURCES:.c=.o)
ASMSOURCES = agas_boot.asm
ASMOBJECTS = $(ASMSOURCES:.asm=.o)

all: $(TARGET)

$(TARGET): $(OBJECTS) $(ASMOBJECTS)
	$(LD) $(LDFLAGS) -o $@ $^

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

%.o: %.asm
	$(AS) $(ASFLAGS) $< -o $@

clean:
	rm -f $(OBJECTS) $(ASMOBJECTS) $(TARGET)

.PHONY: all clean
