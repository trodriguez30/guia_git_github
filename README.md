# Guia de Git y Github

## Resumen del curso de Git y Github de Platzi

### Git

#### Iniciar git
- **git init** #iniciar un repositorio.
#### Configurar git
- **git config –-global user.name “nombre”** #Configurar git con tu nombre.
- **git config –-global user.email “email”** #Configurar git con tu email.

#### Del Working Directory al Staging Area.

- **git add –A** #Agrega todos los archivos que hayan sufrido cambios (creados, modificados, eliminados).

- **git add -n [file or directory]** #Simula el agregado de un archivo o directorio al **Staging Area** pero la verdad no lo hace.

- **git add .** #Agrega los archivos creados y modificados, PERO NO los eliminados.

- **git add -u** #Agrega los archivos modificados y eliminados, PERO NO los creados.

#### Estado de archivos del Working Directory al Staging Area.

- git status #Muestra el estado de los archivos o directorios (**Rojos**: Working directory. **Verde**: Staging Area).

#### Staging Area

- **git rm --cached [file or directory]** #Elimina un archivo o carpeta del **Staging Area** y lo deja en el **Working Directory**.

- **git rm -f [file or directory]** #Forza la eliminación de un archivo o carpeta del **Staging Area** tanto así que hasta lo borra del **Working Directory**.


#### Del Staging Area al Repositorio local.

- **git commit –m “mensaje”** #Compromete los archivos del **Staging Area** y los guarda en el **Repositorio Local** (El mensaje debe ser descriptivo).

- **git commit –amend**  #concatena nuevos cambios a un commit previo.

#### Etiquetas

- **git tag –a [versión] –m “mensaje”** #Etiqueta el estado actual del proyecto, hasta el último commit.

- **git tag –l** #Listar todas las etiquetas

- **git tag [versión] [SHA-1]** #Etiquetar commit por medio del SHA-1

- **git tag –d [versión]** #Borrar una etiqueta

- **git tag –f –a [versión] –m “mensaje” [SHA-1]** #Renombrar un tag de un commmit con el SHA-1.

#### Commits

- **git log** #Listar commits

- **git log –-oneline** #Resume los commits en una línea.

- **–-graph** #Muestra los diferentes commits en las ramas o bifurcaciones con un asterisco.

- **git commit –[número]** #Permite ver los últimos [numero] commits.

- **git checkout [SHA-1]** #Movernos entre commits con el SHA-1. Movernos en el tiempo para ver el estado del proyecto en ese commit.

#### Cambios entre versiones

- **git diff [SHA-1]** #Revisa los cambios que se han hecho entre la versión actual y la colocada en el comando.

- **git diff [versión1 SHA-1] [versión2 SHA-1]** #Revisa los cambios entre los 2 commits colocados, comparando los cambios del primer SHA-1 con los del segundo.

#### Resetear proyecto

- **git reset –-soft [SHA-1]** #Resetea el proyecto a partir del commit indicado, mantiene los cambios en el **Staging área, NO** borra nada.

- **git reset –-mixed [SHA-1]** #Resetea el proyecto a partir del commit indicado, mantiene los cambios en el **Working directory, NO** borra nada.

- **git reset –-hard [SHA-1]** #Regresa hasta el commit del [SHA 1], borra los archivos del **Staging Area y del Working Directory**.

**Nota:** Tener cuidado con el **reset –hard** porque borra todos los cambios, pero puedes salvarlos si tienes los **SHA-1** de los commits. Se recomienda tener los commits guardados en un archivo para evitar pérdidas en el proyecto.

#### Configurar el editor de texto

- **git config –-global core.editor "code --wait"** #Configuración para Visual Studio Code.

#### Ramas

- **git branch [Nombre]** #Crear una nueva rama.

- **git branch –l** #Listar las ramas.

- **git branch –d [Nombre]** #Borrar las ramas.

- **git branch –D [Nombre]** #Forzar el borrado de las ramas.

- **git branch –m [nombre_actual] [nombre_nuevo]** #Renombrar ramas.

- **git checkout [nombre]** #Movernos a una ramas.

- **git checkout –b [nombre]** #Crear una rama y moverse enseguida a ella.

#### Mezclar ramas

Primero hay que ubicarse en la rama principal donde se van a agregar todos los cambios. Por lo general es la master.

- **git merge [nombre]** #Mezcla la rama indicada en el comando con la principal.

#### Resolver conflictos

Escoger con cuál de los cambios quiero quedarme:

Buscar los archivos con conflictos. Aparecerá así la parte del conflicto:

	<<<<<<< HEAD

	#Código original de la rama

	=======

	#Nuevo código

	>>>>>>> BRANCH-NAME

- Escoger cuales cambios deben quedarse y guardar los cambios en los archivos.

- Agregar los cambios con git add –A.

- Generar un commit para confirmar los cambios.

#### Guardar cambios temporalmente

- **git stash** #Guarda modificaciones de manera temporal, pero si confirmarlo. Permite agregar cambios al limbo de git para poder cambiar entre ramas sin llevar los cambios (los archivos tienen que estar en el Staging Area).

- **git stash list** #Muestra la lista de todos los stash.

- **git stash drop stash@{numero}** #Permite borrar el stash indicando su número.

- **git stash apply** #Aplicamos el último cambio al proyecto.

- **git stash apply stash@{numero}** #Aplicamos un cambio en específico indicando su número.

#### Cambiando commit de rama

- **git cherry-pick [SHA-1]** #Permite cambiar un commit de una rama a otra con el SHA-1. Hay que ubicarse en la rama donde queremos ubicar el commit.

#### Ignorar archivos

- Crear un archivo .gitignore.
- Abrir en el editor.
- Colocar el nombre de los archivos que se quieren ignorar (ej: key.js).
- Agregar cambios con git add –A.
- Generar commit para confirmar los cambios.


### Github

#### Clonar repositorios

- **git clone [HTTP/SSH]** #Clonar un repositorio en nuestro computador.

#### Hacer fork de un repositorio.

Permite hacer una copia del repositorio original a nuestra cuenta.

#### Añadir llave SSH a Github

- **ssh-keygen –t rsa –b 4096 –C “email”** #Crear una llave con el mismo email que tienes registrado en Github.

Copiar llave, pegar y guardar en Github settings à SSH and GPG Keys a New SSH key.

#### Añadir un repositorio remoto al local

- **git remote add origin [HTTP/SSH]** #Enlazar repositorio remoto al local.

- **git remote remove origin** #Eliminar enlace con repositorio.

#### Traer y enviar cambios desde el repositorio remoto

- **git fetch origin master** #Traer cambios del repositorio remoto como una nueva rama.

- **git merge origin/master** #Mezclar rama traída con el fetch con el master.

- **git merge origin/master master --allow-unrelated-histories** #Por si da error el commando anterior.

- **git pull origin master** #Trae cambios del repositorio remoto (combinación del fetch y merge)

- **git push origin master** #Enviar cambios a la rama master del repositorio remoto.

- **git push origin [rama]** #Enviar cambios a la rama indicada del repositorio remoto.

- **git push origin master –tags** #Enviar los tags creados de la rama master al repositorio remoto.
