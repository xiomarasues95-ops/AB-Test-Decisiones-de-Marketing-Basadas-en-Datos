# 📊 Pruebas A/B — Optimización de Marketing

> **Autor:** Xiomara Suescun Naizaque | Data Analyst Junior  
> **Herramientas:** Python · Pandas · NumPy · Matplotlib · SciPy  
> **Tipo de análisis:** Priorización de hipótesis (ICE/RICE) + Pruebas A/B + Análisis Estadístico

---

## 📌 Contexto y Objetivo

Una tienda online buscaba incrementar sus ingresos. En colaboración con el departamento de marketing, se recopiló un conjunto de hipótesis orientadas a mejorar el rendimiento del negocio.

El proyecto tuvo dos objetivos principales:

1. **Priorizar hipótesis** usando los frameworks **ICE** (Impact, Confidence, Ease) y **RICE** (Reach, Impact, Confidence, Effort) para identificar cuáles tenían mayor potencial antes de implementarlas.
2. **Analizar un test A/B** para evaluar si los cambios implementados generaron mejoras estadísticamente significativas en conversión e ingresos.

---

## 🗂️ Dataset

| Dataset | Descripción |
|---------|-------------|
| `hypotheses_us.csv` | Hipótesis con parámetros de impacto, alcance, confianza y esfuerzo |
| `orders_us.csv` | Registro de órdenes con fecha, grupo, ingresos y usuario |
| `visits_us.csv` | Registro de visitas diarias por grupo |

---

## 🔧 Metodología

**Paso 1 — Priorización de hipótesis**  
Cálculo de scores ICE y RICE para cada hipótesis y comparación de resultados entre ambos frameworks.

**Paso 2 — Data Cleaning**  
Estandarización de nombres de columnas, corrección de tipos de datos y verificación de duplicados.

**Paso 3 — Análisis exploratorio del test A/B**  
Visualización de ingresos acumulados, tamaño promedio de pedido, tasa de conversión diaria y distribución de pedidos por usuario.

**Paso 4 — Detección de outliers**  
Análisis de percentiles 95 y 99 para identificar usuarios con comportamiento atípico (más de 2 pedidos) y pedidos de alto valor (> $900.90).

**Paso 5 — Pruebas estadísticas**  
Prueba Mann-Whitney U para evaluar significancia estadística en conversión y tamaño promedio de pedido, con datos en bruto y datos filtrados.

---

## 📊 Hallazgos Principales

### 🔢 Priorización de hipótesis
- **RICE** destacó: agregar formulario de suscripción, bloques de recomendación de productos y nuevos canales de tráfico
- **ICE** destacó: lanzar promoción con descuentos, nuevos canales de tráfico y formulario de suscripción
- Ambos frameworks coinciden en que **nuevos canales de tráfico y formulario de suscripción** son prioridades altas

### 📈 Comportamiento del test A/B
- El **Grupo B tomó la delantera** en ingresos acumulados entre el 17 y 21 de agosto de 2019
- La tasa de conversión del Grupo A disminuyó y se estabilizó, mientras la del **Grupo B aumentó y se mantuvo más alta y estable**
- La mayoría de usuarios realizó **entre 1 y 2 pedidos**; muy pocos superaron los 5
- El 95% de las transacciones fue menor a **$435.54**; solo el 1% superó **$900.90**

### 🧪 Resultados estadísticos

| Métrica | Datos sin filtrar | Datos filtrados |
|--------|-------------------|-----------------|
| **Conversión — p-valor** | 0.01679 (< 0.05) ✅ Significativo | 0.00845 (< 0.05) ✅ Significativo |
| **Ganancia de conversión Grupo B** | +13.8% | +17.8% |
| **Tamaño promedio de pedido — p-valor** | 0.692 (> 0.05) ❌ No significativo | — |
| **Diferencia tamaño de pedido** | +25.2% | — |

---

## 💡 Recomendaciones

1. **Detener el test y declarar al Grupo B como ganador** — la diferencia en conversión es estadísticamente significativa tanto con datos en bruto como filtrados
2. **Implementar los cambios del Grupo B** en toda la plataforma, ya que generó una mejora sostenida y consistente en la tasa de conversión
3. **No basar decisiones en el tamaño promedio de pedido** — la diferencia del 25.2% no es estadísticamente significativa y probablemente esté influenciada por valores atípicos
4. **Monitorear los outliers** — los usuarios con más de 2 pedidos y transacciones superiores a $900.90 pueden distorsionar métricas futuras
5. **Priorizar la implementación del formulario de suscripción y nuevos canales de tráfico** — ambos frameworks los identifican como hipótesis de alto impacto

---

## ✅ Conclusión

El test A/B demostró que el **Grupo B supera al Grupo A** en tasa de conversión de manera estadísticamente significativa (+17.8% con datos filtrados). La decisión recomendada es **detener el test y adoptar la versión B** como estándar en la plataforma. El análisis previo con frameworks ICE y RICE permitió identificar las hipóteses con mayor potencial, validando el enfoque de priorización antes de la implementación.

---

## 📁 Estructura del Proyecto

```
📦 AB-Test-Marketing-Analysis
 ┣ 📓 Test_AB.ipynb        # Análisis completo en Python
 ┣ 📄 README.md            # Resumen ejecutivo del proyecto
```