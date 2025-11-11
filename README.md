# README – Tarea de Evaluación Módulo 3: Seguridad Lógica

## 1. Descripción general

Este proyecto corresponde a la Tarea de Evaluación del Módulo 3 de Seguridad Lógica.  
El objetivo es aplicar técnicas de protección de la información mediante:

- Control de accesos con ACL en Windows.
- Cifrado simétrico y asimétrico.
- Verificación de integridad mediante hashes.
- Organización documental para facilitar la revisión del trabajo.

El repositorio incluye la estructura completa utilizada en la actividad: archivos originales, archivos cifrados, claves, hashes y capturas de los procesos.

---

## 2. Estructura del proyecto

El repositorio está organizado de forma clara para facilitar la corrección:
```
/
├── DocumentosSeguros/
│ ├── originales/ → Archivos sin cifrar.
│ ├── cifrado_asimetrico/ → Archivos cifrados con OpenPGP (Kleopatra).
│ ├── cifrado_simetrico/ → Archivos cifrados con AES Crypt.
│ ├── hashes/ → Hashes SHA-256 de los archivos.
│ └── clave_publica/ → Clave pública exportada para cifrado.
│
├── Actividad 3. Powerpoint con capturas del proceso
│
│
└── README.md
```

---

## 3. Control de acceso con ACL (Windows)

Se creó la carpeta `DocumentosSeguros` y se configuraron tres usuarios locales con distintos permisos.

### Usuarios creados
net user tecnico /add
net user gerente /add
net user externo /add

### Asignación de permisos

- tecnico: lectura y escritura.
- gerente: solo lectura.
- externo: sin acceso.

Se deshabilitó la herencia para evitar permisos heredados:
icacls C:\DocumentosSeguros /inheritance:d
Permisos asignados manualmente
Las capturas correspondientes se encuentran en el documento Actividad3..

---

## 4. Cifrado aplicado

### 4.1 Cifrado asimétrico (OpenPGP – Kleopatra)

Los archivos de la carpeta `originales/` fueron cifrados mediante OpenPGP.

Características:

- Tipo: asimétrico.
- Cifrado con clave pública.
- Descifrado con clave privada.
- Archivos resultantes almacenados en `cifrado_asimetrico/`.
- La clave pública se encuentra en `clave_publica/`.

Este método es adecuado para intercambiar información sin exponer claves privadas.

---

### 4.2 Cifrado simétrico (AES Crypt)

Se aplicó cifrado simétrico a varios archivos mediante AES Crypt.

Características:

- Tipo: simétrico.
- La misma contraseña se utiliza para cifrar y descifrar.
- Archivos generados almacenados en `cifrado_simetrico/`.

Este sistema es rápido y eficaz, pero requiere proteger la contraseña utilizada.

---

## 5. Verificación de integridad (SHA-256)

Los hashes SHA-256 se generaron usando:
certutil -hashfile archivo.txt SHA256 > nombre_hash.txt

Los resultados se encuentran en la carpeta `hashes/`.

Se comprobó que cualquier alteración, incluso mínima, en el archivo original genera un hash completamente diferente, lo que demuestra su utilidad para verificar integridad.

---

## 6. Conclusiones sobre seguridad aplicada

- El control de acceso limita correctamente el acceso según roles.
- El cifrado simétrico es sencillo pero requiere buena protección de la contraseña.
- El cifrado asimétrico permite compartir datos de forma segura sin exponer claves sensibles.
- Los hashes permiten detectar alteraciones en archivos.
- La organización del repositorio facilita auditorías y revisión de la actividad.

---

## 7. Conclusión final

La práctica integra todos los elementos básicos de la seguridad lógica: permisos, cifrado e integridad.  
La estructura del proyecto permite comprobar de manera clara y ordenada cada parte del ejercicio.



