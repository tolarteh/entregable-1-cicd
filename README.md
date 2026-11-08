# entregable-1-cicd

## Integrantes
Tomas Olarte Hernandez

## PREGUNTAS

1. ¿Qué eventos configuraste para disparar tu workflow y por qué?

**R1:** Configuré 3 eventos: push a rama main, workflow_dispatch y pull_request a rama main. Esto permite que el workflow se ejecute automáticamente si toco main por un push directo o a través de un pull_request y que pueda manualmente ejecutarlo también (con el dispatch).

2. ¿Qué sistema operativo utiliza el runner `ubuntu-latest` y por qué puede ejecutar tu workflow aunque tu computadora sea Windows o macOS? ¿Qué relación tiene el runner con el shell de los pasos `run`?

**R2:** Linux 7.0.0-1019-azure, podemos ejecutar el workflow porque el runner es un docker con el sistema operativo escogido y el `run` se hace en el shell del sistema operativo escogido (shell o powershell dependiendo de lo escogido).

3. Menciona al menos 3 acciones pre-construidas del Marketplace de GitHub Actions **no mencionadas en este material**. Excluye `actions/checkout`, `actions/setup-python`, `actions/upload-artifact` y `aws-actions/configure-aws-credentials`, aunque alguna solo aparezca como ejemplo conceptual. Describe qué hacen y para qué sirven.

**R3:**

- `super-linter/super-linter@v9.0.0` nos trae una colección de linters y analizadores de código listor para usar sobre el código del repo.
- `google-github-actions/deploy-cloudrun@v3` nos permite desplegar a Google Cloud Run un contenedor o directamente desde la fuente dando como resultado la URL del servicio desplegado.
- `slackapi/slack-github-action@v4.0.0` permite enviar datos a Slack o ejecutar comandos de slack CLI.
- `anthropics/claude-code-action@v1` action de propósito general para que Claude Code pueda trabajar con GitHub PRs y los issues.
- `aws-actions/configure-aws-credentials@v4` permite actualizar el código y la configuración de una función Lambda de AWS, admite .zip e imagenes de contenedores almacenadas en Amazon ECR.

4. ¿Qué es un secreto en GitHub Actions y para qué se usa? ¿Cómo lo usarías en tu workflow?

**R4:** Un secreto es una variable con el valor oculto/cifrado, que se puede usar para pasar valores que no quiero almacenar en el repo o en texto plano en alguna otra parte. Es perfecto para almacenar llaves de APIs como de AWS para desplegar, APIs de IA como AWS Bedrock o Gemini que no quiero que me usen otros por fuera de la aplicación.

5. Reflexiona sobre el uso de GitHub Actions en tu flujo de trabajo diario. ¿Qué tareas automatizarías? ¿Por qué?

**R5:** En mi trabajo diario uso ADO Pipelines, pero para el emprendimiento definitivamente lo usaré para automatizar code review de agentes como Claude Code (porque GitHub Copilot ya está integrado), avisos de que algo falló o que hay warnings en los canales que uso normalmente (WhatsApp o Google Chat) y para el despliegue automático a nubes, actualmente vamos a usar AWS, específicamente las Lambdas.
